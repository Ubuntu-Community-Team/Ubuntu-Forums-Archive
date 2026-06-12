---
title: "[SOLVED] instaling Xubuntu along side existing Ubuntu and GRUB"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by erfahren on 2007-12-23
I currently am dual-booting with Windows and Ubuntu. I made some space to install Xubuntu at the end of my drive. I already have GRUB installed to my MBR and GRUB resides in my existing Ubuntu filesystem.

When I go install Xubuntu (with LiveCD) will it give me an option to see if GRUB is already present?

should I opt out of installing GRUB all together and just manually add Xubuntu to my (Ubuntu's) /boot/grub/menu.lst ? 

or how exactly does that work?

(I'd research this more but kind of just want to get it going!)

---

### Post by logos34 on 2007-12-23
One thing is for certain: if you want to keep your existing ubuntu grub you do NOT want to accept default grub install in Xubuntu because it will overwrite the MBR.  If the Xubuntu live cd installation is anything like ubuntu, then you will come to a "Ready to Install' screen (after the partitioning section), and you will be able to change to location for grub by hitting "Advanced" button lower right, then changing the default '(hd0)' to your xubuntu root partition.  Use the format '/dev/sda4' or whatever your xubuntu root partition is.  

Then you can add xubuntu entry manually to ubuntu menu.lst.

---

### Post by erfahren on 2007-12-23
thanks, I'll watch for that. I wasn't sure where that option was.

I'm sure there's a way to get GRUB to pick up Xubuntu automatically, maybe through GRUBs command line. I'll go look at hermanzone's GRUB page once I get it installed.

thanks again

---

### Post by erfahren on 2007-12-24
just wanted to post back on what I found out on setting up GRUB's menu.lst for another (x)ubuntu install after the fact -- (just in case anyone else wants the info).

on [hermanzone's GRUB page](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems), he explains a way using the symlinks in xubuntu's root directory (which are already there) to boot its lastest kernel.
> 
3. Symlink boot entry
A third method that works very well would be to make an boot entry that will boot the other Linux by it's symlinks, and not refer to it's kernel or ramdisk specifically. Almost all Linux operating systems have symlinks to the kernel and initrd.img files in the root of their filesystems. A few might not. Obviously you will only be able to use this method if there are such symlinks provided, or if you can make them yourself.
The advantage of symlink booting is that it is very reliable. Even if there is a problem with the GRUB menu in the other operating system and you cannot boot that OS any other way, symlink booting will almost always work. 
Here's an example of a symlink boot entry,
```

title        Ubuntu Edgy Eft
root         (hd0,5)
kernel       /vmlinuz root=/dev/hda6 ro quiet splash
initrd       /initrd.img
boot

```
Where: Edgy Eft is a Linux operating system on partition number 6.

Can you see that I have altered the 'kernel' line to refer simply to to /vmlinuz, which is a symlink, rather than a specific kernel like '/boot/vmlinuz-2.6.15-23-386'?
Also, the initrd line has been simplified to '/initrd.img' rather than a specific file like '/boot/initrd.img-2.6.15-23-386'.
The symlinks always point to the most up to date kernel and initrd.img files, so there is no need to worry about updating your GRUB menu after a kernel update in your other system when you are using symlink booting.

I just added another one for recovery mode.

It works well and was a pretty easy fix!

(Edited in) --- so above the "BEGIN AUTOMAGIC KERNELS LIST" section, I just put in:
```

title        Xubuntu 7.10 - Gutsy Gibbon 
root         (hd0,7)
kernel       /vmlinuz root=/dev/sda8 ro quiet splash
initrd       /initrd.img
boot

title        Xubuntu 7.10 - Gutsy Gibbon (recovery mode)
root         (hd0,7)
kernel       /vmlinuz root=/dev/sda8 ro single
initrd       /initrd.img
boot

```

---

### Post by logos34 on 2007-12-24
> **erfahren said:**
> just wanted to post back on what I found out on setting up GRUB's menu.lst for another (x)ubuntu install after the fact -- (just in case anyone else wants the info).
...

I just added another one for recovery mode.

It works well and was a pretty easy fix!

Yep, symbolic link (or [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") method in the case of another distro) works great

As for this issue:
> I'm sure there's a way to get GRUB to pick up Xubuntu automatically, maybe through GRUBs command line.
you have to add it manually, unless you had a separate /boot, in which case update-grub would scan and add any new kernels to the menu.lst

---

