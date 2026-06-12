---
title: "Quick question about grub and kernel panic"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by BFG on 2011-03-24
I have a new acer machine which runs fine on 10.10 mythbuntu desktop livecd.  Install seemed fine.

Then I ran an update and on reboot I get a kernel panic error.  Research on this reveals it as a very deep subject which can consume many hours, so I opted to reinstall.

This time with ubuntu 10.10. I've tried different CDs, liveusb. Same errors.

So, the question is this - where do I concentrate my efforts - somewhere ubuntu doesn't like this machine, or grub.  Does a reinstall overwrite the grub install too? Or do I have a bogus grub install I need to purge before I will get anywhere.

Thanks.

---

### Post by Kirboosy on 2011-03-24
> **BFG said:**
> So, the question is this - where do I concentrate my efforts - somewhere ubuntu doesn't like this machine, or grub.  Does a reinstall overwrite the grub install too? Or do I have a bogus grub install I need to purge before I will get anywhere.

Thanks.


The GRUB should automatically be reinstalled/written on a fresh install. If its running fine before you upgrade the kernel I would just leave it at that kernel until you find out more about the issue. You may also want to try installing an older kernel (but still newer than the stock Ubuntu 10.10 kernel)

~Caboose

---

### Post by BFG on 2011-03-25
> **Caboose885 said:**
> The GRUB should automatically be reinstalled/written on a fresh install. 

Thanks Caboose, that's a big help.

---

### Post by Quackers on 2011-03-25
At what point is the kernel panic happening?
Do you have only one operating system installed? If so, hold down the shift key whilst booting and see if the grub menu appears. If it does, choose the old kernel from the grub menu and see if that still boots.

---

### Post by BFG on 2011-03-28
Directly after grub

I'm going crazy with this.  The machine is an acer Z5610 all-in-one.  I've configured a dual-boot with windows 7. 

LiveCD and liveUSB need a modprobe to be able to work,but work fine.  
I configured the partitions manually, / on ext4 and swap
The install works fine, but on update, something gets screwed at grub level.

kernel panic not syncing vfs. unable to mount root fs unkown block (0,0)

Kernel is 2.6.35-28.  I've tried (via liveUSB + chroot) updating initframs and grub and even re-installing the kernel . No difference.

I'm starting to wonder if it's anything to do with the acer recovery partition


Edit:  I noticed that the liveCD loads kernel 2.6.35.22-generic.  I tried a fresh install and made sure I didn't check "download updates".  The result was another install with kernel 2.6.35-28, which has the same panic problem.

Is there any way I can step back to 2.6.35.22 ?

---

### Post by BFG on 2011-05-07
Found the solution here:
[http://ubuntuforums.org/showthread.php?t=1502709&highlight=acer+z5610](http://ubuntuforums.org/showthread.php?t=1502709&highlight=acer+z5610)

Change BIOS to disable memory hole mapping

---

