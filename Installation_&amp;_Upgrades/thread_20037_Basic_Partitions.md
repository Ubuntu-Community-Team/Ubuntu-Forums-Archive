---
title: "Basic Partitions"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by Nepherim on 2005-03-14
I have 2Gb free for a Ubuntu install. I want to keep things relatively simple. 

1] Other Linux ditruibutions recomment a partitions for Boot, Swap, Home, Root. If I go this route, Root get used for the Ubuntu install, and Home is for my own files?

2] Given my relatively low space:
Boot: 32Mb
Swap: 512MB
Home: Whatever is left
Root: How much does Ubuntu need?

Thanks,

 ~ ~ Dave

---

### Post by Buffalo Soldier on 2005-03-14
I hate to break it to you but 2 Gbyte is too small for Ubuntu. The minimum recommended is 3.5 Gbyte for default install.

But maybe you can try using custom install and only installing the software that you really need. (type **custom** at the command prompt once you boot the installation CD)

With that low space I wouldn't partition it that way. Rather just two partitions: Swap and Root (/)

---

### Post by Nepherim on 2005-03-14
3Gb is the minimum for which one of the partitions (if I were able to go with my original schema)? I presume Root?

---

### Post by Buffalo Soldier on 2005-03-15
According to [Ubuntu Installation Guide - Memory and Disk Space Requirements](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/ch02s05.html)> You must have at least 32MB of memory and 110MB of hard disk space. For a minimal console-based system (all standard packages), 250MB is required. If you want to install a reasonable amount of software, including the X Window System, and some development programs and libraries, you'll need at least 400MB. **For a more or less complete desktop system, you'll need a few gigabytes.**
I'm assuming what you're interested is the complete default install. Which in my situation took about 1.9 Gbyte (root, home and everything but not including swap).

Therefore the 2.5 to 3 Gbyte is the reasonable minimum for the complete default desktop install.

But I hope you are not discouraged. There are still ways to use Ubuntu with limited harddisk space.

---

### Post by Nepherim on 2005-03-15
A little discouraged, but it does sound like a custom install might work okay, so I may give that a go. It's either that or switch to Gentoo.

---

### Post by tanawana on 2005-03-15
If I get you correctly, you can start with this approach and add what you really desire.

[http://www.ubuntulinux.org/support/documentation/howto/miniRAM](http://www.ubuntulinux.org/support/documentation/howto/miniRAM)
and
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

I have a "full" system under 2G but I do not use gnome or such, but rather prefer a tweaked TWM

---

### Post by Nepherim on 2005-03-15
Okay, I freed up some space. I now have a total of 4.5Gb for Ubuntu. Going back to my original scheme:
Boot: 32Mb 
Swap: 512MB
Root: 4Gb
Home: Whatever is left for my files

Do I need the Boot? If so is this where I point Grub to?
Root is where I'd map / to. Correct?

---

### Post by Buffalo Soldier on 2005-03-15
A quick check:
```

 Boot:   32 MB  =  0.003 Gb
 Swap:  512 MB  =  0.5   Gb
 Root:             4     Gb
---------------------------
Total:             4.5+  Gb
---------------------------

```
That's more than the 4.5 Gb limit that you have set. What I would suggest is```

 Swap:  512 MB  =  0.5 Gb
 Root:             1.5 Gb
 Home:             2.5 Gb
-------------------------
Total:             4.5 Gb
-------------------------

```

MBR is the default place for installing GRUB.

Yes, **/** is where you mount the *root filesystem*.

---

### Post by Nepherim on 2005-03-16
[QUOTE=Buffalo Soldier]A quick check:
```

 Boot:   32 MB  =  0.003 Gb
 Swap:  512 MB  =  0.5   Gb
 Root:             4     Gb
---------------------------
Total:             4.5+  Gb
---------------------------

```
That's more than the 4.5 Gb limit that you have set. What I would suggest is```

 Swap:  512 MB  =  0.5 Gb
 Root:             1.5 Gb
 Home:             2.5 Gb
-------------------------
Total:             4.5 Gb
-------------------------

```

MBR is the default place for installing GRUB.

Yes, **/** is where you mount the *root filesystem*.[/QUOTE]
 At this point, I'm just going to use you scenario, but I'd like to understand the purpose of these partitions.

Using both your scenario, and mine, the Ubuntu s/w is installed in the Root.
In Home is just my work files, config files. Any s/w or applications in there?
In my scenario, what is in the Boot partition?

 ~ ~ Dave

---

### Post by Buffalo Soldier on 2005-03-16
[QUOTE=Nepherim]Using both your scenario, and mine, the Ubuntu s/w is installed in the Root.
In Home is just my work files, config files. Any s/w or applications in there?
In my scenario, what is in the Boot partition?[/QUOTE]

True. **/home** contains your personal files, config files, new themes, icons and etc. No software / applications.

The reason I suggest having a separate partition for **/home** is that IF by any chance you want/need to reinstall your GNU/Linux your personal settings and files will remain intact and safe in the separate **/home** partition.

Here's a bit of info on **/boot** from [Getting Started with Linux - Lesson 4](http://www.linux.org/lessons/beginner/l4/lesson4e.html)
> **The /boot directory**

Doing: cd /boot will get you into the /boot directory. You will not find any boots or shoes or footwear of any kind there. That's where the Linux kernel usually is. Power users may change the location of the kernel for reasons of their own (they may prefer /shoe), but it is normally placed there on most systems. You will eventually have to use this directory, because you may need to use two or more different types of kernels in the future. That will be taken up in a more advanced lesson.

Other suggested reading: [Getting Started with Linux - Course Material](http://www.linux.org/lessons/beginner/toc.html) and the howto for beginners from my signature.

---

### Post by Nepherim on 2005-03-16
Thanks for the links, and the responses. Based on this info, the Kernel is different to the Ubuntu s/w and apps. So in the scenario proposed by BuffaloSoldier:  
Swap:  512 MB 
Root:   1.5 Gb
Home:   2.5 Gb

Root holds the kernel, and thus serves the same purpose as Boot (in my scenario). It may just be a little more complex later if I decide to have >1 kernel. Is that right?

Last question (promise). Is 1.5Gb really going to be enough for Ubuntu s/w? Based on prior info in the thread it sounded like I'd need more.

---

### Post by Buffalo Soldier on 2005-03-21
[QUOTE=Nepherim]Last question (promise). Is 1.5Gb really going to be enough for Ubuntu s/w? Based on prior info in the thread it sounded like I'd need more.[/QUOTE]
 I think you've got that one right. Maybe it should be the other way around. Root: 2.5 Gb and Home: 1.5 Gb. Here's what i've been using```
Filesystem	Size Used Avail Use% Mounted on
/dev/hda2	4.4G    1.4G   2.8G    34%    /
/dev/hda3	4.5G    138M   4.1G    4%     /home
```

---

