---
title: "PXE installation problem"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by thegladaitor on 2010-04-07
I am trying to install via PXE boot. Here is the scenario .

Server : Windows 7 

Tftpd Setup done . I have also installed apache and extracted the alternate iso file to the home directory ( where index.html) usually resides . 

Client : Laptop 

I install via PXE and it reaches a point where it asks for archive , I give the IP of my windows machine and .... try to give various directories but I get the error 

"Bad archive mirror error" 

It tries to find some Release file ...


I really dont know what to do . 


Another user explains what I did - Except that he says he gave IP and it works smoothly ! Doesnt it ask for a directory ? 

Quote 

I have DHCP/TFTP part of the install running with no problem, but I'm also trying to serve the packages from the same Windows machine running mini web server. I mount the ubuntu-6.10-alternate-i386.iso image, point the web server to it's root and boot the target PC. Install runs OK, I select location, keyboard, for archive location I enter IP of the Windows machine with the running web server and install continues by copying packages, but it fails to find libstdc++6, libsigc++2, ntpdate, vim-common and vim-tiny. I've tried several times, it's only those 5 pkgs, that the installer can't get. I've checked the exported image and the packages are of course there. Anyone having an idea what's wrong? Thanks.

Quote




Here is the output of my localhost://


Index of /

.disk/
README.diskdefines
cdromupgrade
dists/
doc/
install/
isolinux/
md5sum.txt
pics/
pool/
preseed/
ubuntu
ubuntu-10.04-beta1-alternate-i386.iso
Help

---

### Post by dstew on 2010-04-08
The problem seems to be that the client cannot access the internet. I do not know how your network is configured, but the client needs to know the gateway address. I assume your DHCP/TFTP server is the only DHCP server on your network. You might need to configure it to provide the correct gateway address to the client, especially if you have the gateway somewhere else, like in your router. If your server is not the gateway, you cannot use its own IP address.

Can you provide a link to the installation method you are using? It might help to see exactly what you are trying to do. I see you have put the alternate .iso on the server, so maybe you do not need internet access to install the system. But, it seems the installer is looking for internet access, because that is where the archive mirror is.

---

### Post by kalohr on 2010-08-25
try to setup a web server

put the necessary files for the installation at the www directory

configure the preceed file to use [server ip]/[www content path] as a mirror 

worked for us...

---

