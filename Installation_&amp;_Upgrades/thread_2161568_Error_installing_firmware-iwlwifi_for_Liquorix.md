---
title: "Error installing firmware-iwlwifi for Liquorix"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by alberto666 on 2013-07-11
I have just installed the Liquorix ([http://liquorix.net/](http://liquorix.net/)) kernel to have BFQ Scheduler support (which IMHO should be included in Ubuntu).

Since it is kernel 3.9.9 version, somethings differ, but almost everything seems to work better and fine.

However, I found a problem during installation regarding iwlwifi:
Package configuration                                                          
                                                                               
[INDENT] &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring linux-image-3.9-9.dmz.1-liquorix-amd64 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; 
 &#9474;                                                                           &#9474; 
 &#9474; Required firmware files may be missing                                    &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; This system is currently running Linux 3.8.0-26-generic and you are       &#9474; 
 &#9474; installing Linux 3.9-9.dmz.1-liquorix-amd64.  In the new version some of  &#9474; 
 &#9474; the drivers used on this system may require additional firmware files:    &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; iwlwifi: iwlwifi-3160-6.ucode, iwlwifi-7260-6.ucode                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Most firmware files are not included in the system because they do not    &#9474; 
 &#9474; conform to the Debian Free Software Guidelines. You may need to           &#9474; 
 &#9474; reconfigure the package manager to include the contrib and non-free       &#9474; 
 &#9474; sections of the package archive before you can install these firmware     &#9474; 
 &#9474; files.   [/INDENT]

I tried installing it using their firmware-iwlwifi source, but I got no luck:

[INDENT]sudo apt-get install firmware-iwlwifi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  firmware-iwlwifi
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/3,578 kB of archives.
After this operation, 7,364 kB of additional disk space will be used.
(Reading database ... 423650 files and directories currently installed.)
Unpacking firmware-iwlwifi (from .../firmware-iwlwifi_0.36+nmu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/firmware-iwlwifi_0.36+nmu2_all.deb (--unpack):
 trying to overwrite '/lib/firmware/iwlwifi-5000-5.ucode', which is also in package linux-firmware 1.106
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firmware-iwlwifi_0.36+nmu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

Any idea of how to solve this firmware installation?

Thanks!!!

---

### Post by dino99 on 2013-07-11
you might need to download & install them manually
[http://wireless.kernel.org/en/users/Drivers/iwlwifi#Download](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Download)

---

