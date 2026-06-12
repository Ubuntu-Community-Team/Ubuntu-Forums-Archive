---
title: "Broken /sbin/init"
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by salis on 2005-08-02
](*,) 
I'm stuck in a cycle:
:: Install Ubuntu
:: Boot errors
:: Research errors
:: Install Ubuntu
:: Same boot errors
:: ...

I am installing Hoary on a USB HDD with a 10G ext3 partition (also tried reiserfs).
During the install I chose to write the Grub bootloader to the MBR of the HDD.
Other than that everything else is standard.

After Grub starts to initialise linux I get the following error:
# pivot_root: No such file or directory
# /sbin/init: 428: Cannot open dev/console: no such file
# Kernel Panic

I understand that this is likely caused because my initrd.img doesn't contain something it needs (ext3? scsi? usb?). I don't have a working linux distro to build a new initrd.img. And the Ubuntu LiveCD doesn't let me run a terminal - that's a whole other issue.

I've read a whole heap of articles where people have the same or similar problem, however, either the workaround hasn't worked for me; or I haven't had the right tools.

I'm using the standard initrd.img-2.6.10-5-386.
Is there a newer/recompiled version I should be using?
I noticed when installing in expert mode I was given an option of 3 initrd images, have I chosen the wrong one?

Thanks in advance,
Salis

---

### Post by salis on 2005-08-02
Still the same cycle and still  ](*,) 

This article helped - [http://ubuntuforums.org/showpost.php?p=42546&postcount=14](http://ubuntuforums.org/showpost.php?p=42546&postcount=14)

I've now made a new initrd:
:: boot install cd
:: reinstall ubuntu
:: ctrl-alt-f2 into terminal
# chroot /target
# rm /boot/initrd.img-2.6.10-5-386
# mkinitrd -o /boot/initrd.img-2.6.10-5-386 2.6.10-5-386
:: ctrl-alt-f1 back to installer
:: finish install

This still gives me the same result:
# pivot_root: No such file or directory
# /sbin/init: 428: Cannot open dev/console: no such file
# Kernel Panic

Sometimes the Kernel Panic is preceeded by a lot of 'no such file' and 'bad magic' related errors as the kernel fails to identify the file systems and HDDs.

Even when the Kernel Panic is preceeded by recognised devices, HDDs, and reiserfs modules are loaded... it still ends in a Kernel Panic.

Should my next step be to repackage the kernel?
Will doing this from the install CD result in anything better than the existing default Kernel?

---

### Post by salis on 2005-08-02
:grin: Broke out of the cycle.

It's only once I've been writing to the forum that I've pieced together the complete solution in the forum.

Here's the article that helped - [http://ubuntuforums.org/showthread.php?postid=266745&highlight=external+hdd#post266745](http://ubuntuforums.org/showthread.php?postid=266745&highlight=external+hdd#post266745)
Props to 'propagandhi'... If your having the same/similar issue then search the forums for his posts and you'll find several working solutions.

It's basically adding a few more steps to the mkinitrd process in order to get the right modules in there. I have no idea why they're not in there by default, but once they're in its all working great.

Cheers,
Salis

---

