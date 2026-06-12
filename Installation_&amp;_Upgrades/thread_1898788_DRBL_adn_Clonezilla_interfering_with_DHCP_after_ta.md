---
title: "DRBL adn Clonezilla interfering with DHCP after taking/deploying an image"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by HBED on 2011-12-22
Hello and Merry Xmas all,
I'm trying to get DRBL, Clonezilla and DHCP all to run on a single server. Let me explain in more detail. I have a single server which as well as a file store is also running LDAP, DNS and DHCP. On the end of this server, I will be running approx. 30 machines in a classroom type environmnet.
I have DRBL and CLonezilla configured and running on the server which I want to use to take an image of a ubuntu desktop build, and then deploy that image to other machines on the network. So far so goo.
The process of taking and deploying the image works well. However, once the image has been taken or deployed, the client machines no longer have access to the internet, and it appears to be all down to dhcp. I am using the 192.168.99.0 subnet to run drbl and take/deploy images. I am using the 192.168.75.0 subnet to connect to the internet. (The router address is 192.168.75.5)
I have noticed that after running drblpush, the dhcp conf file is completly overwritten. I understand that this needs to be done to issue the drbl addresses on the 99 subnet for imaging purposes, but when the client machine comes uo, it retains the same IP address on the 99 subnet.
I have tried adding the following to dhcp conf file to allow the issue of the 75 subnet range and therefor allow network connectivity again...
 
subnet 192.168.75.0 netmask 255.255.255.0 {
option routers 192.168.75.5;
range 192.168.75.50 192.168.75.199;
}
 
I have then restarted the dhcp service on the server adn rebooted the client machine, but to no avail. An ifconfig command on the client machine still shows an IP address from the DRBL 99 range and therefor no internet connectivity is given.
 
I've had a look through the forums and found plenty of issues with DRBL/CLonezilla/DHCP but nothing that quite reflects the same issue as I am having.
 
Any help greatly appreciated. I understand that it's the wrong time of year to expect a quick response so I'll keep battling away at it in the meantime and lookback incase anyone comes up trumps.
 
Thanks one and all,
HBED

---

### Post by HBED on 2012-01-30
I have cobbled together a fix for this. After carrying out the drblpush -i section of preparing clonezilla and drbl, I have had to go back into the dhcpd.conf file and re-add the last few lines at the end of the file. The dhcpd.conf file is overwritten by DRBL during its setup.
I re-added the following:-
 
subnet 192.168.75.0 netmask 255.255.255.0 {
option routers 192.168.75.5;
range 192.168.59.50 192.168.75.199;}
 
[FONT=Verdana]During the image process I found that DHCP is more or less halted. Once Clonezilla [/FONT][FONT=Verdana]is then stopped after the deployment of the image, I restarted the DHCP service which [/FONT][FONT=Verdana]then allowed all the machines to pick up IP addresses and communicate with the rest [/FONT][FONT=Verdana]of the nework.[/FONT]

---

