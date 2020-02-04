# ansible-provision-meraki
Provision Meraki devices with Ansible! (Create Network, Claim Devices, Configure, etc)

## Contributing [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/dwyl/esta/issues)

## Prerequisites
* Ansible 2.7+
* Meraki Devices
* pwgen (installed on Ansible server)

## YML File Customization
There are a few things that you'll need to customize yourself before you run the main playbook. I have what you need to customize layed out below.

* create_office.yml
  * In this file you will need to add in your Meraki API key and your org name for it to be able to continue on with this automation process with ansible. If you're unsure on how to get a Meraki API key please see the link below.  

https://documentation.meraki.com/zGeneral_Administration/Other_Topics/The_Cisco_Meraki_Dashboard_API#Enable_API_access

* claim_devices.yml
  * The only real thing to change in this file is the device names under each "Update".

* create_ssid.yml
  * This configures the SSID for any APs you will be installing as well as randomly generating a RADIUS key using pwgen

    - Under "setup wireless ssid" change the name to what your want your SSID to be called
    - Change host IP addresses under "radius_servers" if you're using radius, if not remove the whole radius_servers section
    - Change the default_vlan_id to whatever you want the SSIDs VLAN to be
  
* configure_switches.yml
  * This file configures switchports on the switches you've defined. Please customize this how you would like changing the names, types and VLAN numbers to how you please.

* configure_vlans.yml
  * This file will configure VLANs on any MX devices you have claimed within the network. Change the names and VLAN IDs accordingly.
 
 
## Running the playbook
Once you have all the files customized to your liking and in the same directory you'll want to target "create_office.yml" with your ansible-playbook command. If you run into error be sure to append -vvv to it for extreme debugging output.
  
