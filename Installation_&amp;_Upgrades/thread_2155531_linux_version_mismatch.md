---
title: "linux version mismatch"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by milchmann2 on 2013-06-18
We recently had drive failures on a production box that also apparently had backup issues.  The last good backup was pretty old.  When I got the box running, I began updates, and boot ran out of space.  I removed all of the unused kernels, and ran apt-get -f install, and it was able to finish installing the kernel that it threw the error in the middle of.
Now the system is telling me this:

user@machine:/# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.41.49) but 3.2.0.48.58 is installed
                Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.48.58 is installed
E: Unmet dependencies. Try using -f.

user@machine:/# sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,732 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.41.49); however:
  Version of linux-image-server on system is 3.2.0.48.58.
 linux-server depends on linux-headers-server (= 3.2.0.41.49); however:
  Version of linux-headers-server on system is 3.2.0.48.58.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

user@machine:/# uname -r 
3.2.0-40-generic

user@machine:/# sudo apt-get install --reinstall grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 grub : Conflicts: grub-pc
        Conflicts: grub-pc:i386
 grub-pc : Conflicts: grub (< 0.97-54) but 0.97-29ubuntu66 is to be installed
 grub2-common : Conflicts: grub (< 0.97-54) but 0.97-29ubuntu66 is to be installed
 linux-server : Depends: linux-image-server (= 3.2.0.41.49) but 3.2.0.48.58 is to be installed
                Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.48.58 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I have absolutely no idea where to go from here...

Thanks for any help or ideas.

---

### Post by milchmann2 on 2013-06-18
After searching on this for hours, I found the solution immediately after posting.


apt-get update 
dpkg --remove linux-server 
apt-get install -f 
apt-get install linux-server

---

### Post by deadflowr on 2013-06-18
If you ran the command given, "apt-get -f install" instead of "apt-get -f dist-upgrade" the problem might been fixed sooner.

---

