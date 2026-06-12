---
title: "Compaq Presario R3000 install problems (using netinstall method)"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by sti_fanatic on 2008-06-18
Hi all-

First of all, I would just like to say that these forums are excellent.  I have used Ubuntu lightly in the past with an old PowerPC Apple laptop I have laying around but that finally bit the bullet, so I am now trying to install 8.04 onto a Compaq Presario R3000.  I have heard that Compaqs are notorious for lockdown issues, but I thought I would have a pretty easy time getting this done.

Boy, was I wrong.

First of all, after much frustration on my part, it turns out that the CD drive on this machine is broken.  So that means using the Live CD I burned is out of te question.  Secondly, I am 99% certain that this particular model does not support USB booting, so there goes that option.

I was relegated into some form of net install.  Apparently I have become spoiled by the wonderful internet of silicon valley, because the connection my parents have in their home in CO is *lucky* to pull 56k down.  Being rather impatient, I opted to follow the instructions in [this](http://ubuntuforums.org/showthread.php?t=28948) thread after discovering that UNetbootin simply did not work and Wubi would take 14 days to download the proper files.

Well, no dice.  I then took the suggestions of another thread and changed the instances of "linux.bin" to "vmlinuz" and got a bit further, past the GRUB screen and into the usual flash of text on a black screen that I have come to be comforted by in Linux.

After a bit though, it all stopped, and then I received this gem:
> 
    Check root= bootrag cat /proc/cmdline
    or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/rd/0 does not exist.  Dropping to a shell!

And then I am given a busybox (I think) shell, from which I reboot.

I am really at a loss here.  I would greatly appreciate any help you guys here can give.

Here is what my menu.lst file looks like (located in C:\boot/grub):
> 
title Ubuntu Installer (hd0,0)
kernel (hd0,0)/boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw--
initrd (hd0,0)/boot/initrd.gz

Ideas?  I might just have to guy buy a new CD drive.  Although I would rather not, I am sort of broke right now.

Thanks again guys!

---

### Post by sti_fanatic on 2008-06-19
Welp, I ended up biting the bullet on Wubi and waiting 40 hours to download the OS.  Worked perfectly.

---

