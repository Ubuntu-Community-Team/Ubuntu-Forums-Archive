---
title: "Can not get PXE boot to finish install"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by HansRing on 2012-04-26
I am trying to install Ubuntu 11.10 server via a PXE boot install. I have a computer that I setup to be the PXE boot server. Configured DHCP and TFTP, and appache2. Copyed my install iso CD to the /var/www/ directory. This is an isolated setup. Even though the 2 computers I am working with are connected together over a LAN they do not have internet access.
 
The system I am trying to install Ubuntu 11.10 server onto starts the PXE load. 
 
1. It gets an IP from the DHCP srv
2. It peforms the TFTP request and pulls down a number of files to include the initrd
3. It starts the installation processes in that I start geting the install question screens.
4. It seems to work up to the where it is looking for a mirror site.
5. For the mirror site I put in the Ip address of the http server.
6. Next question asks for the directy where the mirror image is. I tried it at the default /ubuntu/ and at just / but at this point it justs stops and does not pull any data down from the http server /var/www directory.
7. running tcpdump on the computer hosting the HTTP server I see the computer trying to do the PXE install start a tcp session to the correct WWW port 80. My server responds. but no data is pulled down.
 
Does anyone know what files the initrd is specifically looking for?
 
Or better anyone know what I need to do to get the second part of the install to happen?
 
Thanks

---

