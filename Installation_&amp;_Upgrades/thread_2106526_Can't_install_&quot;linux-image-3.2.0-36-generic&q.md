---
title: "Can't install &quot;linux-image-3.2.0-36-generic&quot;"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by glefix on 2013-01-19
Hello!
This is my problem:

> user@localhost:~$ sudo apt-get upgrade
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.2.0-36-generic but it is not installed
E: Unmet dependencies. Try using -f.

user@localhost:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  linux-image-3.2.0-36-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/38,0 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 493802 files and directories currently installed.)
Unpacking linux-image-3.2.0-36-generic (from .../linux-image-3.2.0-36-generic_3.2.0-36.57_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-36-generic_3.2.0-36.57_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/abi-3.2.0-36-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-36-generic_3.2.0-36.57_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

user@localhost:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-36-generic; however:
  Package linux-image-3.2.0-36-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.36.43); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic
 linux-generic
user@localhost:~$

Thanks!

---

### Post by ibjsb4 on 2013-01-19
Looks like you need to remove some old kernels to make some room.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by steeldriver on 2013-01-19
agreed

> failed in write on buffer copy for backend dpkg-deb during `./boot/abi-3.2.0-36-generic': [COLOR=Red]No space left on device[/COLOR]
No apport report written because the error message indicates a [COLOR=Red]disk full[/COLOR] error

---

### Post by glefix on 2013-01-19
That didn't do it, thanks anyway.

> user@localhost:~$ dpkg --get-selections | grep linux-image
linux-image-3.2.0-23-generic            install
linux-image-3.2.0-26-generic            install
linux-image-3.2.0-30-generic            install
linux-image-3.2.0-31-generic            install
linux-image-3.2.0-32-generic            install
linux-image-3.2.0-33-generic            install
linux-image-3.2.0-34-generic            install
linux-image-3.2.0-35-generic            install
linux-image-generic                install
user@localhost:~$ sudo apt-get purge linux-image-3.2.0-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.2.0-36-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


But I found anoter solution. When is started Synaptic, it said there's a broken package and I should use the filter for broken packages and remove it. Dit that and everything is fine now.

---

### Post by ibjsb4 on 2013-01-19
> **glefix said:**
> That didn't do it, thanks anyway.  But I found anoter solution. When is started Synaptic, it said there's a broken package and I should use the filter for broken packages and remove it. Dit that and everything is fine now.

Glad you figured it out, but for future reference the autoremove command works good.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Remove_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Remove_old_kernels)

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

And 

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

AND welcome to the forums :)

---

