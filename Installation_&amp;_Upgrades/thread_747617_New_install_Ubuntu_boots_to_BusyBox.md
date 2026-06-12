---
title: "New install Ubuntu boots to BusyBox"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by breezey on 2008-04-06
I just installed Ubuntu 8.04 (32bit) on my PC with SATA drive. I installed Ubuntu as dual boot with Windows Vista 64bit. The reason I installed Ubuntu 8.04 (beta) was because I could not even boot the 7.10 CD.

Installation was successful but I boots to BusyBox. Any help will be appreciated. Thanks.

---

### Post by chromedome on 2008-04-07
I get the same thing.  I'd done a clean Gutsy install just recently, nothing non-standard except WINE.  Everything seems good, it boots up to the splash screen, but then after "Pong" goes back and forth for 90 seconds or so it kicks me out to Busybox.

The instructions given here didn't work for me: my system errored out on apt-get update (didn't record the error message, don't have time now, will do so later). [http://ubuntuforums.org/showthread.php?t=600644]("http://ubuntuforums.org/showthread.php?t=600644")

---

### Post by chromedome on 2008-04-07
Never mind.  

Breezey, going back to the earlier kernel version seems to do the trick (did for me, anyway).

Reboot your computer, and hit "Esc" to get into the GRUB menu.  Choose the older kernel (last two digits 14, rather than 15), and you should boot properly.

Found this elsewhere on the site.  Neglected to bookmark the thread or note the user, but thank you whoever you are.

---

### Post by chromedome on 2008-04-11
Okay, a couple of things.

First, how would I go about setting the ".14" version of the kernel as default under GRUB?  It's kind of a pain, having to babysit if/when I reboot.

Second, I'm getting an error in my update manager.  The update to liblaunchpad-integration1 won't install, giving me the message: 

> E: /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb: trying to overwrite `/usr/share/icons/hicolor/16x16/apps/lpi-bug.png', which is also in package liblaunchpad-integration0


Also, it tells me that I have two packages broken, but when I run Synaptic and use the "broken" filter, it doesn't find anything.  Are these little quirks related to my running the older kernel?

---

### Post by twist2b on 2008-04-11
startup manager allows you to choose your default boot system.
get it here:
[https://sourceforge.net/projects/startup-manager/](https://sourceforge.net/projects/startup-manager/)

enjoy.

---

### Post by Pumalite on 2008-04-11
For your apt-get problem, try:
sudo dpkg --configure -a 
sudo apt-get -f install 
sudo apt-get update
sudo apt-get upgrade

---

### Post by chromedome on 2008-04-14
Pumalite: trying to get my updates manually gives me the same error (slight changes in wording).

Twist2B: Can't install startup manager, 'cause of the other problem.

---

### Post by Pumalite on 2008-04-14
You need to post the entire output of my commands for me to figure out if I can help you.

---

### Post by warp99 on 2008-04-14
> **breezey said:**
> I just installed Ubuntu 8.04 (32bit) on my PC with SATA drive. I installed Ubuntu as dual boot with Windows Vista 64bit. The reason I installed Ubuntu 8.04 (beta) was because I could not even boot the 7.10 CD.

Installation was successful but I boots to BusyBox. Any help will be appreciated. Thanks.

The initrd.img file may be corrupt. You can boot to the Ubuntu install CD, mount the drive, chroot into the drive and rebuild the file if needed. Example:

Ubuntu is installed to sda2, which is partition two of disk one. Boot to the Ubuntu install disc and open a terminal to issue the following:

Make a directory to mount the drive:
```
sudo mkdir /media/sda2
```
mount the drive to the directory
```
sudo mount /dev/sda2 /media/sda2
```
chroot into the mounted directory
```
chroot /media/sda2
```
now the root drive is the installed partition. Move to the /boot directory to verify the files are there:
```
cd /boot && ls -l
```
output is:
```

-rw-r--r-- 1 root root  417807 2008-02-11 22:30 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   67666 2008-02-11 22:30 config-2.6.22-14-generic
drwxr-xr-x 3 root root     480 2008-02-13 11:03 grub
-rw-r--r-- 1 root root 7707427 2008-04-06 11:55 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root  103204 2007-07-30 18:13 memtest86+.bin
-rw-r--r-- 1 root root 1052627 2008-02-11 22:30 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1743752 2008-02-11 22:30 vmlinuz-2.6.22-14-generic
```
update the initrd.img:
```
sudo update-initramfs -u -v
```
then reboot the computer. If the update does not work you can try again and create a new initrd.img with the following command
```
sudo update-initramfs -c -v -k $(uname -r)
```

---

### Post by chromedome on 2008-04-15
> **Pumalite said:**
> You need to post the entire output of my commands for me to figure out if I can help you.

Here we go, then...

> fred@fred-desktop:~$ sudo dpkg --configure -a 
[sudo] password for fred: 
dpkg: dependency problems prevent configuration of python-launchpad-integration:
 python-launchpad-integration depends on liblaunchpad-integration1 (>= 0.1.17); however:
  Package liblaunchpad-integration1 is not installed.
dpkg: error processing python-launchpad-integration (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on liblaunchpad-integration1 (>= 0.1.17); however:
  Package liblaunchpad-integration1 is not installed.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.22.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.22.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-launchpad-integration
 liblpint-bonobo0
 evolution
 evolution-exchange
 evolution-plugins 

> fred@fred-desktop:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  liblaunchpad-integration1
The following NEW packages will be installed:
  liblaunchpad-integration1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/17.7kB of archives.
After this operation, 172kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 115819 files and directories currently installed.)
Unpacking liblaunchpad-integration1 (from .../liblaunchpad-integration1_0.1.18_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb (--unpack):
 trying to overwrite `/usr/share/icons/hicolor/16x16/apps/lpi-bug.png', which is also in package liblaunchpad-integration0
Errors were encountered while processing:
 /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

sudo apt-get update = no errors

> fred@fred-desktop:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  liblpint-bonobo0: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  python-launchpad-integration: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
E: Unmet dependencies. Try using -f.


So, I ran apt-get -f install again, and got:

> fred@fred-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  liblaunchpad-integration1
The following NEW packages will be installed:
  liblaunchpad-integration1
0 upgraded, 1 newly installed, 0 to remove and 286 not upgraded.
5 not fully installed or removed.
Need to get 17.7kB of archives.
After this operation, 172kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main liblaunchpad-integration1 0.1.19 [17.7kB]
Fetched 17.7kB in 2s (7074B/s)              
(Reading database ... 115819 files and directories currently installed.)
Unpacking liblaunchpad-integration1 (from .../liblaunchpad-integration1_0.1.19_i386.deb) ...
Replacing files in old package liblaunchpad-integration0 ...
Setting up liblaunchpad-integration1 (0.1.19) ...

Setting up liblpint-bonobo0 (0.1.18) ...

Setting up evolution (2.22.1-0ubuntu1) ...

Setting up evolution-exchange (2.22.1-0ubuntu1) ...

Setting up evolution-plugins (2.22.1-0ubuntu1) ...
Setting up python-launchpad-integration (0.1.18) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


Does that mean that it worked, this time?

---

### Post by Pumalite on 2008-04-15
Yes.

---

### Post by chromedome on 2008-04-16
:P Yeah, the 240-odd MB of updates were a bit of a giveaway.

'Course, by the time those finished downloading on my crappy satellite connection, I was in bed asleep.

Thank you kindly, Pumalite.  I appreciate the assistance.

---

### Post by Pumalite on 2008-04-16
You are welcome. Good luck.

---

