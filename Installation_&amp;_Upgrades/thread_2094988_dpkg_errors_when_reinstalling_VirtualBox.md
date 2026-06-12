---
title: "dpkg errors when reinstalling VirtualBox"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by DeanM1134 on 2012-12-15
Ubuntu 12.10 64-bit
AMD-A3620 APU
8GB of system memory
Gnome 3
So I previously installed VirtualBox on my computer, for the sake of running a Windows 7 virtual machine so I didn't constantly have to restart. Everything worked fine, setup was easy, the VM got installed and running fine but I wanted to be able to use seamless mode and to do that I had to install its Guest Additions. After virtualBox failed to install this (in hindsight probably my own fault for not looking up the correct way to do it), I figured it wouldn't hurt to just uninstall and reinstall the program. I've had to do it before with other programs to update this, so I saw no problem. I uninstalled it via '--purge autoremove'. When I try to open the same .deb I downloaded with the software center (opening it with the software center, I downloaded it off the website) package I used to install it the first time, or if I use apt-get to install the application I get this error: 
```
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 234581 files and directories currently installed.) 
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.2-81494~Ubuntu~quantal_amd64.deb) ... 
dpkg: error processing /home/marcus/Downloads/virtualbox-4.2_4.2.2-81494~Ubuntu~quantal_amd64.deb (--install): 
 trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions-iso 4.1.18-1 
dpkg-deb (subprocess): decompressing archive member: lzma write error: Broken pipe 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg-deb (subprocess): cannot copy archive member from '/home/marcus/Downloads/virtualbox-4.2_4.2.2-81494~Ubuntu~quantal_amd64.deb' to decompressor pipe: failed to write (Broken pipe) 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for shared-mime-info ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Errors were encountered while processing: 
 /home/marcus/Downloads/virtualbox-4.2_4.2.2-81494~Ubuntu~quantal_amd64.deb 

```
Restarting didn't help, trying to update or uninstall and reinstall dpkg just leads to it telling me no packages were changed etc. this is getting pretty frustrating, as I'd really like to be able to use VirtualBox as apposed to VMWare or something like that as VMWare  feels much slower and clunkier to me and exporting my machine to it's .ova format doesn't work out entirely well. I've also deleted and redownlaod the package from the virtualbox website a few times to be sure it isn't that, to no avail.

---

### Post by SeijiSensei on 2012-12-15
This error suggests you might not be using sudo to install:

> trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso'

---

### Post by DeanM1134 on 2012-12-15
> **SeijiSensei said:**
> This error suggests you might not be using sudo to install:
I used sudo apt-get for everything, but i'll try again and make sure i'm root with sudo su first just to be sure.

---

### Post by DeanM1134 on 2012-12-15
it's still not letting me, even if I'm root and using sudo su. The same errors are thrown at me

---

### Post by DeanM1134 on 2012-12-15
After removing the file it said it couldn't overwrite and trying again, I get this from the terminal:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libasprintf0c2:i386 libcroco3:i386 libgomp1:i386 libgsoap2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/59.8 MB of archives.
After this operation, 132 MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 236658 files and directories currently installed.)
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb (--unpack):
 trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions-iso 4.1.18-1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@marcus-p7-1254:/home/marcus# sudo apt-get install virtualbox-4.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libasprintf0c2:i386 libcroco3:i386 libgomp1:i386 libgsoap2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/59.8 MB of archives.
After this operation, 132 MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 236658 files and directories currently installed.)
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb (--unpack):
 trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions-iso 4.1.18-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by DeanM1134 on 2012-12-16
I really need some help with this, i'm clueless as to what to do

---

### Post by NM5TF on 2012-12-16
it might be best to use Software Center to remove VB, then re-install it again using Software Center....it does NOT install the guest additions
automatically...you need to go to the Oracle site & install them...you ALSO
need to be sure that you install the guest additions for the CORRECT version
of VB that you are using....

Tommy

---

### Post by SeijiSensei on 2012-12-17
The most reliable way to install VirtualBox is to follow the "Debian-based" instructions on the [VB Linux download page]("https://www.virtualbox.org/wiki/Linux_Downloads").  Add the repository and its key as described there, then try 
```

sudo apt-get update
sudo apt-get purge virtualbox-* 
sudo apt-get install virtualbox-4.2

```
The OS will then manage VB updates like it does all other software in repositories.

---

### Post by DeanM1134 on 2012-12-17
> **SeijiSensei said:**
> The most reliable way to install VirtualBox is to follow the "Debian-based" instructions on the [VB Linux download page]("https://www.virtualbox.org/wiki/Linux_Downloads").  Add the repository and its key as described there, then try 
```

sudo apt-get update
sudo apt-get purge virtualbox-* 
sudo apt-get install virtualbox-4.2

```The OS will then manage VB updates like it does all other software in repositories.
Thank you, this world flawlessly and I have my guest additions installed now as well. The way I was trying to do it before was wrong in every sense anyway.

---

### Post by bradian on 2012-12-31
Thank you - this helped me as well and relieved me of a lot of potential stress!

---

