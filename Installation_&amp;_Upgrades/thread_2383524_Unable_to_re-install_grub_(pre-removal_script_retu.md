---
title: "Unable to re-install grub (pre-removal script returned error exit status 10))"
date: 2018-01-26
forum: Installation &amp; Upgrades
---

### Post by zetafiles on 2018-01-26
**backstory:**

I'm running root on ZFS and when I installed it only worked with the debian unstable version of grub .
Last week running "apt upgrade" on a server (which also runs root on ZFS) made it not reboot because it was incompatible with the grub version.
Installing the ubuntu version of grub fixed the problem though.

Now I want to do the same on my PC.

I have already run "sudo apt purge grub grub-pc grub-common"


**problem:**

Z@zpc:~$ sudo apt install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version (2.02-2).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 grub-pc : Depends: grub-common (= 2.02-2)
           Depends: grub2-common (= 2.02-2)
           Depends: grub-pc-bin (= 2.02-2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Z@zpc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
grub-pc
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 592 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 244857 files and directories currently installed.)
Removing grub-pc (2.02-2) ...
dpkg: error processing package grub-pc (--remove):
subprocess installed pre-removal script returned error exit status 10
Errors were encountered while processing:
grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

Z@zpc:~$ sudo dpkg --configure -a

Z@zpc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
grub-pc
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 592 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 244857 files and directories currently installed.)
Removing grub-pc (2.02-2) ...
dpkg: error processing package grub-pc (--remove): subprocess installed pre-removal script returned error exit status 10
Errors were encountered while processing:
grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

Z@zpc:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
grub-pc : Depends: grub-common (= 2.02-2)
Depends: grub2-common (= 2.02-2)
Depends: grub-pc-bin (= 2.02-2)
E: Unmet dependencies. Try using -f.

---

### Post by zetafiles on 2018-01-26
I prepared a live-usb and tried rebooting ... and it unexpectedly did actually boot.
Ubuntu detected the error. But when I was about to report it I got a message about grub not being part of Ubuntu !?
Probably because the grub version I'm trying to remove comes from debian unstable. 
So how do I fix this !?

Z@zpc:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 grub-pc : Depends: grub-common (= 2.02-2)
           Depends: grub2-common (= 2.02-2)
           Depends: grub-pc-bin (= 2.02-2)
E: Unmet dependencies. Try using -f.

Z@zpc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  grub-pc
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 592 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 245692 files and directories currently installed.)
Removing grub-pc (2.02-2) ...
dpkg: error processing package grub-pc (--remove):
 subprocess installed pre-removal script returned error exit status 10
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

