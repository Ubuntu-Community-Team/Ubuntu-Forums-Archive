---
title: "Virtualbox - non free"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dunbrokin on 2009-10-21
There seems to be a bug in the Kernel in relation to virtualboxd....this appears to have happened with previous upgrades also.

The error message I get is 

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

---

### Post by etnlIcarus on 2009-10-21
Make sure the DKMS and linux-headers-generic packages are installed. It's not a kernel bug, you just don't have the necessary tools on your system, for DKMS to automatically re-compile the vbox kernel modules, whenever a kernel bugfix is released.

Until the next kernel update, you'll have to do it manually, though.

---

### Post by RedG on 2009-10-21
Do you have this DKMS-package?
I use Virtualbox with Karmic, and have done so for awhile, with no problems.  I have had this in Jaunty, but not now.
Unfortunately I don't remember how I corrected this. But I guess tried to install the DKMS-package and ran '/etc/init.d/vboxdrv setup' ...

Good luck!

---

### Post by hal10000 on 2009-10-21
The virtualbox kernel driver has to be recompiled after each kernel-upgrade.
You can simply do this with 
```
sudo etc/init.d/vboxdrv setup
```
Before you start a virtual machine you also have to ensure your vboxdrv is running. You can do this with
```
sudo etc/init.d/vboxdrv start
```

---

### Post by dunbrokin on 2009-10-21
sudo: etc/init.d/vboxdrv: command not found

It does not seem to be on my system!!

DKMS is already installed....

---

### Post by etnlIcarus on 2009-10-21
It's /etc/, not etc/.

---

### Post by dunbrokin on 2009-10-21
pj@indulgence:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for pj: 
sudo: /etc/init.d/vboxdrv: command not found

---

### Post by hal10000 on 2009-10-21
Of course it's /etc, sorry

> sudo: /etc/init.d/vboxdrv: command not found
If /etc/init.d/vboxdrv does'nt exist, then your virtualbox-installation is damaged or incomplete, which should not happen if you installed it with your package manager

---

### Post by dunbrokin on 2009-10-21
I downloaded the deb from the Sun site and installed it.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads), the Karmic i386.

---

### Post by RedG on 2009-10-21
Then I would try to re-install it.

---

### Post by dunbrokin on 2009-10-21
> **RedG said:**
> Then I would try to re-install it.

I just did....no change...same result, same problem.

---

### Post by etnlIcarus on 2009-10-21
paste the output of:
```
ls /etc/init.d/
```

---

### Post by RedG on 2009-10-21
What version of Virtualbox is you using?
It seems like just befor an update to 3.0.8 there was this problem, but after the update this was solved...
[http://forums.virtualbox.org/viewtopic.php?f=7&t=22922](http://forums.virtualbox.org/viewtopic.php?f=7&t=22922)

---

### Post by hal10000 on 2009-10-21
> It seems like just befor an update to 3.0.8 there was this problem

I'm running the 3.0.8 version (on jaunty) and it's fine.

---

### Post by dunbrokin on 2009-10-21
umountfs
cron                pulseaudio         umountnfs.sh
cryptdisks          rc                 umountroot
cryptdisks-early    rc.local           unattended-upgrades
cryptdisks-enable   rcS                urandom
cups                README             usplash
dbus                reboot             vboxdrv.dpkg-bak
dkms_autoinstaller  rsync              virtualbox-ose
dmesg               rsyslog            wicd
dns-clean           rsyslog-kmsg       wpa-ifupdown
gdm                 samba              x11-common
grub-common         saned
hal                 screen-cleanup

I am running 3.08...I had the OSE version running on Jaunty with no problem. I notice here that I have the OSE version but not the non-free version despite installing it twice....any suggestions?

---

### Post by Vanishing on 2009-10-21
> **dunbrokin said:**
> There seems to be a bug in the Kernel in relation to virtualboxd....this appears to have happened with previous upgrades also.

The error message I get is 

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

i actually took vboxdrv off from startup services because i dont run it everytime i log in.
to use it
do this:
> sudo /etc/init.d/vboxdrv start
everytime after you update your kernel, do this
> sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv start
 and you are good to go

---

### Post by RedG on 2009-10-21
I can only tell what I would do.
First I would take a backup of my virtual machines.
Then I would uninstall virtualbox-OSE with "-purge" option to remove all old config-files, hence the backup. Maybe the virtual machines is left even with the purge option, but just to be safe.
Then I would do a fresh install of virtualbox.

---

### Post by hal10000 on 2009-10-21
> umountfs
cron pulseaudio umountnfs.sh
cryptdisks rc umountroot
cryptdisks-early rc.local unattended-upgrades
cryptdisks-enable rcS urandom
cups README usplash
dbus reboot **vboxdrv.dpkg-bak**
dkms_autoinstaller rsync **virtualbox-ose**
dmesg rsyslog wicd
dns-clean rsyslog-kmsg wpa-ifupdown
gdm samba x11-common
grub-common saned
hal screen-cleanup

if this is the content of your /etc/init.d directory, then something went horribly wrong with your virtualbox-installation.
You have two files supposedly from an old or your ose installation lying around. You may rename the [COLOR="Red"]vboxdrv.dpkg-bak[/COLOR] file to [COLOR="Red"]vboxdrv[/COLOR]. Maybe you have luck and it works, but i think the best is to purge your virtualbox installation, and then  add this repository to your /etc/apt/sources.list:
```

deb http://download.virtualbox.org/virtualbox/debian karmic non-free

```
After adding the key you can install virtualbox with your package-manager:
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add - 
```

---

### Post by toor58 on 2009-10-21
There is nothing wrong with VB. The error reads missing pae. Have to wait till final release to use VB in karmic. that is all.

cheers

---

### Post by jeremyswalker on 2009-10-21
> **toor58 said:**
> There is nothing wrong with VB. The error reads missing pae. Have to wait till final release to use VB in karmic. that is all.

cheers

I have no issue using VB in karmic. How would waiting till the final release have any effect?

---

### Post by dunbrokin on 2009-10-21
OK, thank you all for your help, I will wait a day or two to see what the new build throws up and will purge the old ose version.

---

