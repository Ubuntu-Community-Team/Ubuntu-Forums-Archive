---
title: "Dual Booth Ubuntu 16.04 CentOS 7"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by AUDIOTEK on 2017-03-08
Lots of info on the net regarding installing both Ubuntu and CentOS on the same machine but nothing is very clear    I'm on my third attemp the closest I got is Ubuntu worked flawlwessly but CentOS would crash soon as I would be on the desktop

Anybody has clear instructions on how to manage that?

Both are fresh installs

My next attempt is to fully install Ubuntu, use Gparted and create a separate partition fror CentOS and install it then upgrade Grub from Ubuntu

Too bad this video is too old the CentOS options look too different now.

I know no LVM when installing Ubuntu

---

### Post by yancek on 2017-03-08
The link below has a pretty detailed explanation on installing CentOS 7 with screeen images.  Don't use LVM and don't let it automatically partition.  There is an option "I will configure partitioning" so select that.  I don't see any option at the site on where to  install the Grub bootloader.  If you get the option to install to the CentOS partition, do that.  When you reboot you should reboot to Ubuntu and from Ubuntu, run:  sudo update-grub and you should watch the output for the CentOS entry.  If CentOS installs Grub to the MBR, then on reboot select the Ubuntu option and re-install Grub to the MBR from Ubuntu, if that's what you want.

[http://www.tecmint.com/centos-7-installation/](http://www.tecmint.com/centos-7-installation/)

All of the above is if you are using the older MBR method rather than UEFI.

---

### Post by AUDIOTEK on 2017-03-08
Does it matter which one I install first?

In Ubuntu should I select LVM or leave it blank?   I just started a fresh install checked LVM it's currently running with LVM enabled.   If no LVM on Ubuntu I'll re-install right away when that install is done

---

### Post by yancek on 2017-03-08
Do you know what LVM is and what it does?  If you are not familiar with it, you likely have problems.  I haven't used it myself so can't really advise for or against but it will be very different from standard partitioning.  It definitely has advantages but not many users do use it so you will need to read up on it and familiarize yourself.

I would suggest you google "how to install multiple systems with LVM Linux" and you should get a number of hits like the site below.  If you don't understand it, don't do it.

[https://www.howtoforge.com/community/threads/howto-install-multiple-distros-on-one-lvm.41465/](https://www.howtoforge.com/community/threads/howto-install-multiple-distros-on-one-lvm.41465/)

---

### Post by AUDIOTEK on 2017-03-08
It's a volume manager   It gives you more flexibility on how to handle your volumes in general    But my question is if I go non LVM on Ubuntu and LVM on CentOS (which is recommended with CentOS) if that could be one of the cause of my problems

---

### Post by QIII on 2017-03-08
I believe that with CentOS, Fedora and RHEL, LVM is the default.  I deliberately choose standard partitioning rather than LVM on Fedora.

If this is a single machine, you are using one disk (or one per distro), and don't need to have partitions cross between multiple devices then do your self a favor:  avoid the downsides and learning curve of LVM and use standard partitioning.

The downsides of LVM become less significant and the upsides more significant for larger-scale installations/enterprises.

---

### Post by Dennis N on 2017-03-08
> **AUDIOTEK said:**
> It's a volume manager   It gives you more flexibility on how to handle your volumes in general    But my question is if I go non LVM on Ubuntu and LVM on CentOS (which is recommended with CentOS) if that could be one of the cause of my problems

You can certainly mix an installation using LVM with one not using it. I have Xubuntu installed using LVM on the same disk as Lubuntu with a standard install (no LVM). In my case, I first did the standard Lubuntu install, then, working from Lubuntu, created the necessary LVM structure in the unallocated space in which to install Xubuntu. You also may need to create a separate standard boot partition for the LVM install. The Ubuntu installer will detect and show the LVM logical volume to be specified as root if you use the "something else" option. The CentOS installer (Anaconda) most likely has this capability too.

---

### Post by AUDIOTEK on 2017-03-08
Great utility to have  Gparted on boot

[http://gparted.org/download.php](http://gparted.org/download.php)

I split my drive in 2   let's see how I can manage that with 2 pre defined partitions

I know it comes with Ubuntu and you can do the same with a live Ubuntu install CD on "Try Ubuntu" but it's good to have   It doesn't care what you have on any of your disks when you push partition it just does it

---

### Post by AUDIOTEK on 2017-03-09
I found the issue.   For some reason I can't install Ubuntu 16.10 so that's why I went to 16.06 and cannot install CentOS 7 so I went to 6.8

it seems it's an issue with the laptop it's a Dell Latitude E6540

I'll look at the BIOS to see if there's a newer one

---

### Post by oldfred on 2017-03-09
That should be an UEFI based system.

My SFF desktop with same generation (Haswell) processor came with Windows 8, updated to Windows 10. I only kept Windows to watch Xfinity DVR.
But I originally installed 15.10 and 16.04 (both)in UEFI mode triple boot without any issues.

Are you installing in UEFI mode?

---

