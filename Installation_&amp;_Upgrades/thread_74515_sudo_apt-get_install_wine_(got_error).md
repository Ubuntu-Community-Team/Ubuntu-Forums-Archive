---
title: "sudo apt-get install wine (got error)"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by AntiMS on 2005-10-11
Im using ubuntu 5.04, and im trying to install wine but i got error message.

when i type this 

root@c7:~# sudo apt-get update
> Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Get:2 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary Release
Get:5 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates Release [16.8kB]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/main Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/universe Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Fetched 34.1kB in 5s (6613B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

root@c7:~# sudo apt-get install wine> 
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  msttcorefonts wine-doc wine-utils binfmt-support
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.9MB of archives.
After unpacking 56.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.0.20050725-winehq-1 [14.9MB]
Fetched 964kB in 30s (31.2kB/s)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package wine.
(Reading database ... 75409 files and directories currently installed.)
Unpacking wine (from .../wine_0.0.20050725-winehq-1_i386.deb) ...
Setting up wine (0.0.20050725-winehq-1) ...

W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

root@c7:~# dpkg -i wine*.deb
> dpkg: error processing wine*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine*.deb


Is there other configuration doesnt set?
Any idea about this..... thanks in advance :D

---

### Post by KLineD on 2005-10-11
> Fetched 34.1kB in 5s (6613B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This indicates that some other process is using the APT database. Are you running synaptic also?. Try closing any other application that uses the apt database and then try again to do sudo apt-get update and install.

Also when you update correctly, you just have to do sudo apt-get install wine to install it, no need to do dpkg -i as that's used when you downloaded a .deb from outside the repositories and want to use dpkg to install it (not this case)

---

### Post by AntiMS on 2005-10-12
hmm, now i know, thanks for the reply.

---

