---
title: "Do 2nd and 3rd installs of Xubuntu on drive = ?option to not install GRUB2 to mbr?"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by mikodo on 2012-08-21
Hi

I want my next clean install (Xubuntu 12.04),  to have extra installs of it on the hard-drive, to experiment with and break, probably.;)

Will I have the option, **to not install GRUB2** **during the subsequent installs**, after the primary (first) install, has GRUB2 installed, with it? 

I will have ["Boot-Repair"]("https://help.ubuntu.com/community/Boot-Repair") installed on the primary, to be sure.

Thanks.

---

### Post by oldfred on 2012-08-22
No, each install normally default to install grub2's boot loader to the MBR and use that install to boot.

If you use manual install or Something else you get a choice on where to install the grub2 boot loader, but there is not a choice to not install. You can install to the same partition, just to in effect not install it. 

In your primary install run this, to find added installs:

sudo update-grub

If it does install, you can boot into your primary and reinstall it to the MBR:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub


grub also remembers where to reinstall on major updates. So you want to change that if not correct, especially for added installs as you do not want them overwriting your main installs grub boot loader.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub


#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions, You can unchoose all and it will not reinstall.

---

### Post by mikodo on 2012-08-22
Thanks oldfred,

I have to ponder what you wrote. Once I understand, I'll follow your advice.

You have never steered me wrong before.

;)

---

### Post by mikodo on 2012-08-22
@oldfred. Actually, your directions were thorough enough, even for me. 

I'll mark it as solved and save your work.

Thanks.

---

### Post by oldfred on 2012-08-22
Glad you figured it out. :)

I am often accused of too much info. My old boss before I retired did that all the time. But I try to make it understandable or at least provide back ground info and/or links for those who may want more.

---

### Post by mikodo on 2012-08-22
> **oldfred said:**
> Glad you figured it out. :)
I am often accused of too much info. My old boss before I retired did that all the time. But I try to make it understandable or at least provide back ground info and/or links for those who may want more.
I for one, am happy to have all the detail.

:)

---

