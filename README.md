# Azuresecurehub with routingintent and forced tunneling
Hi all, this sets up a securehub, a couple of spoke vnets and a firewall spoke vnet. Routing intent is enabled but uses a "Forced tunnel" configuration to force internet traffic out the spoke firewall. More info here: https://learn.microsoft.com/en-us/azure/virtual-wan/about-internet-routing. The location for the resources is limited in this one so it defaults to East US.
This also creates a log analytics workspace and diagnostic settings for the firewall logs for both firewalls. You'll be prompted for the resource group name, your public ip and username and password to use for the VM's. NSG's are placed on the default subnets of each vnet allowing RDP access from your public ip and route tables are added sending traffic to your public ip to the internet. This also creates a logic app that will delete the resource group in 24hrs.

The topology will look like this:
<img width="949" height="738" alt="wvanlabRIwithspokefw" src="https://github.com/user-attachments/assets/689c1346-7fec-4dbc-b5f9-a354c6dcc839" />

You can run Terraform right from the Azure cloud shell by cloning this git repository with "git clone https://github.com/quiveringbacon/Azuresecurehub-routingintent-forcedtunnel.git ./terraform".

Then, "cd terraform" then, "terraform init" and finally "terraform apply -auto-approve" to deploy.
