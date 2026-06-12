---
title: "AMD blew up, need to re-install kernel for intel chip using same instalation of ubunt"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by asus on 2007-02-13
My amd fried.  It was a duron.  I now have the same hard drive, running ubuntu in my p3 box.  I need to get this hd running, i have all my services that i use.  Can i somehow reinstall the kernel with the boot cd?  Someone said a rescue disk.  I have no idea what i can do .. thanks

---

### Post by Yoooder on 2007-02-13
You can save it!  And with a little more info it should be pretty painless.

Couple quick questions:
  Since you say you need a kernel that supports your Intel proc I presume you had a customized kernel compiled specifically for your old Duron, is that correct?

If so, do you have your original kernel still on your harddrive?

If that's the case then you'll just have to do some quick bootloader configuring to run from the stock kernel (which supports almost all hardware).

If not then you should be able to boot a liveCD, chroot into the distro on your drive, and swap out kernels.

In any event, if you post the answers to these questions myself or someone else should be able to give you more specific instructions.

---

### Post by louieb on 2007-02-13
> **asus said:**
> I now have the same hard drive, running ubuntu in my p3 box.  I need to get this hd running, 
You have us both confused. Sow down, take a deep breath and try to describe just what you are trying to do. 
And tell us what you have done so far. 
Did you just put HD from the AMD PC in the P3 PC and try to boot?
Do you have Ubuntu installed on the P3?
Do you need to copy or access data from the AMD's hard drive?

---

### Post by dcstar on 2007-02-13
As a general warning for anyone installing "Restricted" kernels (for CPU or any other changes from default), it is always good policy to leave one of the stock-standard kernels in your system for that "just-in-case" time that may, one day, actually hit you.

In this case it is going to be tricky to install another kernel from a boot CD, it may be easier to do a fresh install on the new hardware with a new disk and then just copy off any relevant data from the old HD.

Because it is a totally different PC there may be issues with video, sound and other hardware differences as well as the kernel which could waste far more time to resolve than doing a fresh install.

---

### Post by asus on 2007-02-14
yeah.. i still have the kernel on the hd.. the HD is untouched actually, i just moved it from the dead computer to the new one

well.. it always updated the kernel, but i dont think i ever modified the kernel or anything.

if not.. how would i chroot ?? 

and if i do have the kernel and i can make some grup changes, what would those be?

Thanks you all

---

### Post by pay on 2007-02-14
> **asus said:**
> yeah.. i still have the kernel on the hd.. the HD is untouched actually, i just moved it from the dead computer to the new one

well.. it always updated the kernel, but i dont think i ever modified the kernel or anything.

if not.. how would i chroot ?? 

and if i do have the kernel and i can make some grup changes, what would those be?

Thanks you allMount the drives ```
# mount /dev/hda3 /mnt/gentoo
# mkdir /mnt/gentoo/boot
# mount /dev/hda1 /mnt/gentoo/boot
```and type something like this ```
# chroot /mnt/gentoo /bin/bash
# env-update
>> Regenerating /etc/ld.so.cache...
# source /etc/profile
# export PS1="(chroot) $PS1"
```This is from the Gentoo handbook. Obviously change the partitions to your partitions.

---

### Post by asus on 2007-02-14
hmm.. thanks you all.. wow.. thats um.. wrong.. oops.. anyway.  let me give that a try.. il let ya all know how it works out.

---

### Post by asus on 2007-02-14
well, now i my computer gets stuck at "waiting for root file system" and never moves on from that point?  Any ideas??  I installed the kernel for the p3.. 686 is it ?

---

### Post by asus on 2007-02-14
also.. i tried installing the regular kernel.. and it still gets stuck at that point

---

### Post by louieb on 2007-02-14
Sounds like you are getting close to a fix.
It also sounds like you need to check /etc/fstab  and make sure it matches up with the display of fdisk -l. 
Don't know if thats the problem but it doesn't hurt to check.

---

### Post by asus on 2007-02-15
when i do an fdisk -l i get // /proct/partitions or whatever cannot be opened.  i looked in the dir.. and there are no files or anything there.  i tried fooling with the fstab file, but no luck.. it sitll gets stuck.. and after waiting for 10 or so min of it being suck, it dumps me to busybox

i get an error at the top that says

alert!  !  /dev/hdc1 does not exist.

i know that usually the device is hda1 .. so i changed that in fstab.. but no luck.. so i have no idea what to do?  any thoughts ?

---

### Post by asus on 2007-02-15
hmm.. i think i fixed it.. i changed the grub.lis to hda1 insted of hdc1 and it seams to be booting.. right now.. its checking dev/shm/root 

il let you know if it starts up :)

---

### Post by Yoooder on 2007-02-15
a random guess at the "root filesystem" error is your fstab.

If your drive is in a new machine it might be at a different device location (instead of being your IDE0 Primary (hda) maybe it's now your secondary slave (hdd)).

If this is the case then either you'll need to plug your harddrive into the same ide port it was using in the old machine, or modify your /etc/fstab file to match it's new location.

---

