---
title: "Replace the DHCP client"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by Mowen on 2005-04-26
Hi all,

I am a beginner with Ubuntu. I have some problem with the default DHCP client (cable connection with dual boot) and would like to replace it by DHCPCD. What commands do I need to type to remove the default one and install the DHCPCD ?

Thanks in advance for your help.

---

### Post by firefox on 2005-04-26
[QUOTE=Mowen]Hi all,

I am a beginner with Ubuntu. I have some problem with the default DHCP client (cable connection with dual boot) and would like to replace it by DHCPCD. What commands do I need to type to remove the default one and install the DHCPCD ?

Thanks in advance for your help.[/QUOTE]
 You can add/remove packets using apt-get.
apt-get install packetName
or apt-get remove packetName

you can look for packages with 'apt-cache search searchString'. or look for the packages on [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

NOTE: you have to edit the /etc/apt/sources.list (uncomment the lines) and do an apt-get update before you can use the commands above.

---

### Post by Mowen on 2005-05-03
Thanks a mil. It has worked.  :)

---

