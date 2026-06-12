---
title: "Kernel vs OS... I'm always confused"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by ABitTooSpicy on 2013-03-21
I just ran an update and my comp started loading directly onto the command prompt with that annoying blinking cursor instead of taking me to my pretty orange login screen... I use Ubuntu 12.04 btw.

So, I rebooted and tried an older kernel and everything worked again... even all the updates were showing up. To fix my "issue" i purged the latest kernel and now it's as if nothing had ever happened... but how can it be?! I'm so confused! =)

What gives? How can everything be there if I am going back to a previous kernel?? The best explanation I found is here: [http://bogdangradinaru.wordpress.com/2010/02/04/kernel-vs-operating-system/]("http://bogdangradinaru.wordpress.com/2010/02/04/kernel-vs-operating-system/")

[IMG]http://bogdangradinaru.files.wordpress.com/2010/02/os2.jpg[/IMG]

So is it bad that I am not running the latest kernel but am running the latest OS?

I'm now on 3.2.0-38-generic-pae

3.2.0-39-generic-pae refused to work but I gave up rather quickly.

---

### Post by tgalati4 on 2013-03-21
Are you running a proprietary graphics module?  If so, then you might need to reinstall that module to get your graphics back after installing the latest kernel.

The older kernels are kept around so you can boot into them if you have a problem with an update.  Think of it as a spare tire.

Wait a few weeks before reinstalling the latest kernel.  Do some research into what changed in it.  Look into your graphics driver.

The operating system contains the kernel and utilities.  Look in /usr/bin and /usr/sbin.  You can upgrade the kernel (minor upgrades only) but keep the same utilities.  Add the graphics server (xorg) and the desktop environment (Unity, Gnome, KDE, XFCE)  and you have a complete operating system.  The kernel is in /boot.  Most of the configuration files are in /etc.

As a general rule, don't upgrade xorg or the kernel unless you need to and you know what you are doing, and you know how to recover from problems.

---

### Post by grahammechanical on 2013-03-21
Some people will have an argument over a question like this. Some say the "Linux OS" and others will argue forcibly that it should be called the "Gnu/Linux" OS. And there is one Grub developer who says that without the boot loader we would not have an OS. So, it should be called the "Grub/Gnu/Linux" OS. 

The fact is that there many components that make up a Linux Distribution. Does it matter if we call it an OS when perhaps it is more accurately a distribution? All the components that we are running are also under constant development. So, what really is the latest OS? For example, Ubuntu 12.10 uses Linux kernel 3.5.0 series and 13.04 uses Linux kernel 3.8.0 series and by the time that 14.04 is released it may have Linux kernel 3.9 or 4.0 series. This kind numbering system is used to keep track of development and to trace back bugs to the code that produces the bug.

Regards.

---

### Post by haqking on 2013-03-21
> **grahammechanical said:**
>  And there is one Grub developer who says that without the boot loader we would not have an OS. So, it should be called the "Grub/Gnu/Linux" OS. 



You might want to remind that developer about Lilo ;-)

To the OP Both Windows and Linux have a kernel, everything around that kernel that  allows us to interact with the hardware is the Operating System, the  software we install into the Operating System is application software.

There are different versions of the Kernel within the Linux world and many different distributions use different kernels in there distro, all the distros are Operating Systems. Strictly speaking Linux refers to the kernel and its variants, then the term distro refers to a kernel that has been taken and configured with lots of software and aesthetics to be "unique" and then branded as  XXXXX distribution.

Peace

---

### Post by ABitTooSpicy on 2013-03-24
Thanks for all the answers!

The conclusion that I have come to: My main machine, that I use for work, will no longer get updated. Every time I run the recommended updates, I have to spend a few hours figuring out how to restore back to previous state... or figure out how to fix the one thing that is now broken that wasn't broken before... =P So no more updates unless something is specifically broken! :)

I have a 2nd machine that I use more as a media center, also running ubuntu 12.04... I'll tinker with that one and continue to learn. Not having access to that machine for a day or two or even a week or two is just fine.

---

### Post by tgalati4 on 2013-03-25
Encountering regressions on a production machine is painful.  It shouldn't happen, but it does.  My own collection of machines have different versions of Ubuntu or Linux Mint, just for that reason.  If something is broken in the latest version, there is usually an older version that still works--so I can still get some work done.

---

