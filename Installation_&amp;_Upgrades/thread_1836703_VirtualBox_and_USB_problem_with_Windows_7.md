---
title: "VirtualBox and USB problem with Windows 7"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by philchambers on 2011-08-31
I could not get USB memory sticks working with a Windows 7 guest on Ubuntu 10.04 64bit and VirtualBox so I installed Ubuntu 11.04 (Natty Narwhal) 64bit in the hope that would work.

I installed VirtualBox (4.0.4_OSE) using the Ubuntu Software Centre and did not expect USB to work but found that Windows XP was fine. This was without the Oracle Extensions Pack.

However, with Windows7 32bit Enterprise, USB is OK with a scanner and printer but not with Memory sticks.  Windows Device manager shows a problem with the 'USB Mass Storage Drive' driver: 'This device cannot start. (Code 10)'.  (In typical Microsoft way this message gives no clue at all to what the problem might be!)  I have tried to update the device driver but Windows says it is up to date.

Installing the Oracle Extensions Pack makes no difference.

I have the same version of Windows 7 working fine on a 32bit Centos system.

I have also tried a completely new Ubuntu installation with the latest VirtualBox from virtualbox.org but that was the same.

Any suggestions please?

---

### Post by haqking on 2011-08-31
> **philchambers said:**
> I could not get USB memory sticks working with a Windows 7 guest on Ubuntu 10.04 64bit and VirtualBox so I installed Ubuntu 11.04 (Natty Narwhal) 64bit in the hope that would work.

I installed VirtualBox (4.0.4_OSE) using the Ubuntu Software Centre and did not expect USB to work but found that Windows XP was fine. This was without the Oracle Extensions Pack.

However, with Windows7 32bit Enterprise, USB is OK with a scanner and printer but not with Memory sticks.  Windows Device manager shows a problem with the 'USB Mass Storage Drive' driver: 'This device cannot start. (Code 10)'.  (In typical Microsoft way this message gives no clue at all to what the problem might be!)  I have tried to update the device driver but Windows says it is up to date.

Installing the Oracle Extensions Pack makes no difference.

I have the same version of Windows 7 working fine on a 32bit Centos system.

I have also tried a completely new Ubuntu installation with the latest VirtualBox from virtualbox.org but that was the same.

Any suggestions please?

You need to create the vboxusers group if it does not exist and make sure you are a member for USB to work in virtual box

read here a little ways down in the linux installation section [http://www.virtualbox.org/manual/ch02.html](http://www.virtualbox.org/manual/ch02.html)

there is a heading called The vboxusers group

---

### Post by philchambers on 2011-09-01
Sorry that I failed to say that I have added myself to the vboxusers group.  Note that I said that USB was fine with XP - that would not be the case if I had not done that.  I have been through all thr trouble-shooting information I can find.

---

### Post by SteDolphin on 2012-10-16
Is there a solution for this topic, I am having exactly the same issue as described ...

USB Sticks are working fine on WinXP Virtual Machines, but not working on any Win7 virtual machines (32 or 64bit)

TKS

Steve

---

### Post by charmingbear on 2013-08-09
Bumping here because:
Same Problem:
Xubuntu 13.04 Host 64Bit
VBox OSE from Ubuntu repos
No Extention Pack (because of OSE)
Guest W7 Pro
Hardware USB 2.0 Controller + USB2.0 Mass storage Devices
All USB Devices work but no Mass storage device
Connection to Guest Works, but W7 says: 
This device cannot start. (Code 10) and is yellow marked.

---

### Post by oldos2er on 2013-08-09
charmingbear, please start a new thread, this one's quite old.

---

