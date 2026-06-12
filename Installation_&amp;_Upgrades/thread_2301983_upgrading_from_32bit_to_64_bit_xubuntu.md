---
title: "upgrading from 32bit to 64 bit xubuntu"
date: 2015-11-06
forum: Installation &amp; Upgrades
---

### Post by bradhaack on 2015-11-06
I'm adding memory and updating to 64 bit xubuntu.  Since the software updater is broken right now I think the best way is for me to get the minimal CD and install that way?   Agreed?    I don't have a DVD writer, so that isn't an option.   Also I'd like to clean up from prior distros,  what can I safely delete?
Any tips to make the process as painless as possible are appreciated.

The main reason I'm doing this is because I've had persistent system issues & was told that 32 bit wasn't supported anymore.   I hope 64 works out bettter.

---

### Post by ubfan1 on 2015-11-06
There must be a misunderstanding somewhere, 32 bit xubuntu is definitely still supported.  Perhaps the confusion is for UEFI machines, which take a LOT more work to make a 32 bit release run because of the bootloader.

---

### Post by grahammechanical on 2015-11-06
Here is the link to 32 bit Xubuntu 15.10

[http://cdimage.ubuntu.com/xubuntu/releases/wily/release/](http://cdimage.ubuntu.com/xubuntu/releases/wily/release/)

Look for xubuntu-15.10-desktop-i386.iso. It is 1 GB in size so it is to large for a CD disk. If the machine does not boot from a USB stick it could mean that the machine is enough to have a 32 bit CPU. So, 64 bit Xubuntu will not work on it. 

It could be that the CPU does not have Physical Address Extensions (PAE). Ubuntu does not support non-pae 32 bit CPUs any more. Is this what you have been told about? Could this be why you have been recommended to use the Minimal CD?

But Lubuntu does give support to certain non-pae 32 bit CPUs that are actually pae CPUs but they don't tell the installer they are. You can read about it.

[URL="https://help.ubuntu.com/community/PAE?action=show&redirect=EnablingPAE"]https://help.ubuntu.com/community/PAE?action=show&redirect=EnablingPAE

[/URL]We really do not have enough information about your hardware or even the version of Xubuntu that is installed. If it is a version that has reached end of life, then that could be the reason why "the software updater is broken."

> Also I'd like to clean up from prior distros,  what can I safely delete?

I have no idea what you are talking about. You need to give us more information about what is installed on that machine and the partition layout.

Regards.

---

### Post by bradhaack on 2015-11-06
> **ubfan1 said:**
> There must be a misunderstanding somewhere, 32 bit xubuntu is definitely still supported.  Perhaps the confusion is for UEFI machines, which take a LOT more work to make a 32 bit release run because of the bootloader.

I have this bug which was never resolved and make my computer almost unusable.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1434557](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1434557)

In one of the replys:
"as 32-bit OSes have a de-emphasis of support upstream, could you please test with a 64-bit OS and advise to the results?"

The computer is a Dell Vostro 260S.   xubuntu 14.4.   When I boot I have options for older OS and KDE.  I'd like to free up disk space and delete those.   What else do you need to know?  I'm not a power user.

There are many files in /boot.   What can I safely delete, or is there a better way to manage that?

---

### Post by ubfan1 on 2015-11-06
Your computer has Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz for a CPU, so it is 64 bit compatible.
You can remove the kernel packages to free up space in /boot.  I use sudo apt-get purge  (list the linux packages)  to remove the unwanted files.

---

### Post by mörgæs on 2015-11-07
If I read the posts correctly you want to erase everything which is installed now. Just choose 'erase entire hard disk' during install. 

32 bit is still supported but I agree that a 64 bit 15.10 is a better choice for your processor.

---

### Post by bradhaack on 2015-11-07
No I do not want to erase everything.   I'll try apt-get purge.
Thanks

---

### Post by Vladlenin5000 on 2015-11-07
I'm afraid you'll have to. You can't "upgrade" to 64-bit. It must be reinstalled. Do your backups and prepare a USB flash drive for the installation (USB boot must be supported - it certainly is for any 15 years old PC or newer).

---

### Post by bradhaack on 2015-11-07
If I have a /home partition on the disk can't I install the new OS in / and leave /home and the rest of the partitions alone?

---

### Post by Vladlenin5000 on 2015-11-07
> **bradhaack said:**
> If I have a /home partition on the disk can't I install the new OS in / and leave /home and the rest of the partitions alone?

Yes :-)
Obs.: /home also stores user and apps settings. I'm not sure about what behavior to expect from certain apps...

---

### Post by oldos2er on 2015-11-07
> **bradhaack said:**
> If I have a /home partition on the disk can't I install the new OS in / and leave /home and the rest of the partitions alone?

That's exactly the advantage of having a separate /home partition. Also makes backups easier, in my opinion.

---

### Post by bradhaack on 2015-11-07
Whats the best/easiest way to handle incompatabilities in the settings that get transferred over in /home?  Just deal with them as they come up?

---

### Post by oldos2er on 2015-11-08
Are you changing to a different OS version, or just changing to 64-bit from 32-bit, same OS? I don't think your /home/user config files care about the bitness of their programs, at least to my knowledge.

---

