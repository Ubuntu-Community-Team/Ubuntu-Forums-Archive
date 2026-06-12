---
title: "Alternate CD netboot -- cannot find valid image"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by roydrager on 2010-07-31
Hi folks, I'm network installing 10.04 lucid 32 bit on my local network using a mounted iso.  (I'm using dhcp3-server, tftp-hpa, and apache2.)  

When I use the netboot files on the alternate CD in /install/netboot/, the installation only gets as far as discovering a linux image on the network.  There is a red screen saying it cannot find a valid linux image.  When I use the netboot files from the stand-alone netboot.tar.gz from the archives, in conjuntion with either alternate iso or desktop iso for the installation files, it recognizes the valid media.  But it gives a blue screen with the message "the installer failed to download a file from the mirror" and options to retry, change mirror, or cancel.  

However, two times out of my many attempts, the installer recognized the iso and started downloading the install files.  Then it crashed.  

Dropping to console, wget is working fine and I'm able to manually download files from apache's /var/www/ubuntu/ directory.  Apache's log from the failed image download looks like this:

> 192.168.0.102 - - [22/Jul/2010:01:46:31 -0700] "GET //dists/lucid/Release HTTP/1.1" 200 2027 "-" "Wget"
192.168.0.102 - - [22/Jul/2010:01:46:31 -0700] "GET //dists/lucid/Release.gpg HTTP/1.1" 200 455 "-" "Wget"


---

### Post by roydrager on 2010-08-04
It turns out my install .iso was corrupt.  Mint 9 (the server) didn't give me a warning when I mounted the iso.  When I finally switched to an Ubuntu box as the server, the console mount command gave the warning "not a valid CD image" and the graphical Archive Manager said the file was corrupt.   

It would have saved me many hours if Mint had issued that warning in the first place.  I'll be sticking with plain old Ubuntu from now on.  I only got the idea to change servers from Mint to Ubuntu because the installation began successfully one time, crashed, and then didn't work the second time using the exact same procedure.  

Anyway, local network install using mounted ubuntu 64 bit alternate iso was completed successfully.

---

