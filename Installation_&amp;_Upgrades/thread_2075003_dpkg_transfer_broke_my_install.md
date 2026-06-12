---
title: "dpkg transfer broke my install"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by unibroker on 2012-10-22
I installed 12.04 64 bit today and it went fine.  I then transferred my packages from 12.04 32 bit and when that completed I had a package that failed to install.  I shutdown and restarted and now bootup doesn't complete; no Unity, no upper right hand corner controls, I can launch the terminal to shutdown but that's about it.

Apparently it's a known bug but I didn't read that it had affected the other filers to the degree my install had been.  I still have my 32 bit install and went to package manager figuring the package would be there since that's the source of my transfer.  I searched using all the parameters but couldn't find it (I was just going to remove it, and transfer the new version).

The package is:  libapt-pkg4.12_0.8.16~exp12ubuntu10.3_i386.deb.  Any ideas why I can't find it in Package Manager?  Here are the last lines, containing the error message, from my transfer.```
dpkg: error processing /var/cache/apt/archives/libapt-pkg4.12_0.8.16~exp12ubuntu10.3_i386.deb (--unpack):
 './usr/share/locale/sk/LC_MESSAGES/libapt-pkg4.12.mo' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libapt-pkg4.12_0.8.16~exp12ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

BTW, after the transfer completed I was going to download Chromium from Software Center but that was missing and Dash couldn't find it.  This was before I rebooted and couldn't get anything but a terminal to shutdown.

---

### Post by neo_1in on 2012-10-22
> **unibroker said:**
> I installed 12.04 64 bit today and it went fine.  I then transferred my packages from 12.04 32 bit and when that completed I had a package that failed to install.

When you say you transferred pkgs from 32bit to 64bit, did you force install them?
The pkg libapt-pkg4.12, like many more, is a package in the default install. Which means your 64bit installation already has it.
I am not 100% sure, but it is not a good idea to install 32 bit pkgs in 64 bit system unless you are sure, specially when they are system files or when corresponding 64 bit packages are already available.
Better install pkgs from proper repositories instead of using the archived pkgs from your 32 bit install.
Try doing 'sudo apt-get install -f' or 'sudo dpkg-reconfigure -a' or 'sudo dpkg --configure -a', see what happens and then get back.

---

### Post by unibroker on 2012-10-22
> **neo_1in said:**
> When you say you transferred pkgs from 32bit to 64bit, did you force install them?
The pkg libapt-pkg4.12, like many more, is a package in the default install. Which means your 64bit installation already has it.
I am not 100% sure, but it is not a good idea to install 32 bit pkgs in 64 bit system unless you are sure, specially when they are system files or when corresponding 64 bit packages are already available.
Better install pkgs from proper repositories instead of using the archived pkgs from your 32 bit install.
Try doing 'sudo apt-get install -f' or 'sudo dpkg-reconfigure -a' or 'sudo dpkg --configure -a', see what happens and then get back.

This is the code that I used for transfer ```
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
```

Maybe I was supposed to upgrade the install before doing the transfer of old packages.

Here is the bug report [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1039685]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1039685")

---

### Post by unibroker on 2012-10-23
> **neo_1in said:**
> When you say you transferred pkgs from 32bit to 64bit, did you force install them?
The pkg libapt-pkg4.12, like many more, is a package in the default install. Which means your 64bit installation already has it.
I am not 100% sure, but it is not a good idea to install 32 bit pkgs in 64 bit system unless you are sure, specially when they are system files or when corresponding 64 bit packages are already available.
Better install pkgs from proper repositories instead of using the archived pkgs from your 32 bit install.
Try doing 'sudo apt-get install -f' or 'sudo dpkg-reconfigure -a' or 'sudo dpkg --configure -a', see what happens and then get back.

I tried your code suggestions but none of them had any effect.  I did a reinstall of the 64 bit this AM and had it automatically install updates.  That was my problem because it had no problem on reboot.  I'm going to try the dpkg transfer again later but I first need to pare it down.

---

### Post by neo_1in on 2012-10-24
> **unibroker said:**
> I'm going to try the dpkg transfer again later but I first need to pare it down.

Erm! don't do it man :P. Or at least make sure you are not overwriting any of the packages already installed. And good luck!

---

