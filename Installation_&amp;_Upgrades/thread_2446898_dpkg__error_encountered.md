---
title: "dpkg : error encountered"
date: 2020-07-08
forum: Installation &amp; Upgrades
---

### Post by turdbird on 2020-07-08
Very short backstory before reading the following commands I gave to my CLi.
1- This is a fresh Ubuntu 20.04 Focal Fossa. The ONLY thing I have done before these commands were given was.
Sudo apt get update. Then Sudo apt get upgrade.
After these commands were given I went onto netacad.com website AKA Cisco's Free web classes. And Downloaded PacketTracer 7.3.
[https://community.cisco.com/t5/network-management/unable-to-install-packettracer-on-ubuntu-20-04/td-p/4074024](https://community.cisco.com/t5/network-management/unable-to-install-packettracer-on-ubuntu-20-04/td-p/4074024)
I then followed the above tutorial to setup packet tracer. Which it runs well now.

Now I type in the following....

 sudo apt upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libjpeg-turbo8 : Breaks: libjpeg-turbo8:i386 (!= 2.0.3-0ubuntu1) but 2.0.3-0ubuntu1.20.04.1 is installed
 libjpeg-turbo8:i386 : Breaks: libjpeg-turbo8 (!= 2.0.3-0ubuntu1.20.04.1) but 2.0.3-0ubuntu1 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

turdbird@SatelliteDish:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libjpeg-turbo8
The following packages will be upgraded:
  libjpeg-turbo8
1 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.
4 not fully installed or removed.
Need to get 0 B/117 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 196365 files and directories currently installed.)
Preparing to unpack .../libjpeg-turbo8_2.0.3-0ubuntu1.20.04.1_amd64.deb ...
Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1.20.04.1) over (2.0.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libjpeg-turbo8_2.0.3-0ubuntu1.20.04.1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libjpeg-turbo8/changelog.Debian.gz', which is different from other instances of package libjpeg-t
urbo8:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg-turbo8_2.0.3-0ubuntu1.20.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

And now when I click on the Software Updater in the GUI to have the OS download updates I get the following....

THE PACKAGE SYSTEM IS BROKEN
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

libjpeg-turbo8: Depends: libc6 (>= 2.14) but 2.31-0ubuntu9 is installed
libjpeg-turbo8:i386: Depends: libc6 (>= 2.7) but 2.31-0ubuntu9 is installed

Essentially I think I am getting the same error message in 2 different manners. One where I am trying to update through the CLi, the other through the GUI.

Does anybody know how I can fix the issue I am currently having? The only reason I did any of this was to be able to run packet tracer to do some Netacad classes. 


Thank you very much in advance!
Also I apologize in advance, because I imagine this is an issue others have encountered before, in which case please just shoot me a link and I will figure it out! Nonetheless, thanks!

---

### Post by Impavidus on 2020-07-08
We had a very similar issue a short while back with libpng on 16.04. That problem wasn't really resolved and we concluded that in that case a fresh install would be best, as the system was in a pretty bad shape overall. If you want to read: [https://ubuntuforums.org/showthread.php?t=2445577](https://ubuntuforums.org/showthread.php?t=2445577)

It appears the package manager has some difficulty handling packages that have both the 64 and 32 bit version installed. I've never been in that position (my system is pure 64 bit). On a 64 bit system you only need 32 bit libraries to deal with third-party precompiled software only available in 32 bit. I guess it's possible to instruct dpkg to force overwriting such files also present in other packages, or temporarily remove one of them.

Not a very elegant solution. I wonder if this should be called a bug...

---

### Post by mearine on 2020-07-17
I had a similar issue too. I solved this problem by the method linked below.[URL="https://unix.stackexchange.com/questions/290836/how-do-i-update-ubuntu-when-package-system-is-broken"]
https://unix.stackexchange.com/questions/290836/how-do-i-update-ubuntu-when-package-system-is-broken[/URL]

---

