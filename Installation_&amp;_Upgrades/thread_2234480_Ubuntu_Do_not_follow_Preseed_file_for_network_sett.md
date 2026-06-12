---
title: "Ubuntu Do not follow Preseed file for network settings"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by Abhijit Navale on 2014-07-15
I am trying to automate Ubuntu installations using Cobbler and preseed.


  I refered this officical sample Seed file for Ubuntu [URL="https://help.ubuntu.com/12.04/installation-guide/example-preseed.txt"]https://help.ubuntu.com/12.04/installation-guide/example-preseed.txt
[/URL]

  I Only edit network related part in this file and now this is my sample.seed file [URL="http://paste.ubuntu.com/7793361/"]http://paste.ubuntu.com/7793361/
[/URL]

  I did not edited anything else. My target machine has two nic. eth0 and eth1. Only eth1 is connected to cobbler server through private network. 

  After booting Ubuntu Mini ISO it asks me to manually select between  eth0 and eth1 and also ask to manually configure ip, netmask and other  details as shown here [http://imgur.com/L2IrAmV](http://imgur.com/L2IrAmV)  But I have already set all these settings in that preseed file.


  I have set my seed file location correctly as /var/lib/cobbler/kickstarts/sample.seed
For testing purpose I disabled second NIC, and only enabled one NIC. Then I manually set the network information. Still ubuntu tries to use dhcp and says can not configure network and halts. Same issue if i use kickstart instead of preseed.

  Kindly help to trouble shoot this issue. How can I make ubuntu to  autoselect eth1 and apply all other networking settings such as ,ip,  netwask etc automatically?

---

