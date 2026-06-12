---
title: "[SOLVED] Preperation for Triple Boot"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by afbase on 2008-06-05
I just switched my primary OS from Vista to Hardy Heron (yay).  Only trouble is that I still NEED adobe products such as cs3.  I want to test which version of windows i like best for this, XP and Vista. 

I made four partitions like so:
```

clinton@clinton-laptop:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00056c30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15204   122126098+  83  Linux
/dev/sda2           15205       17636    19535040   82  Linux swap / Solaris
/dev/sda3           17637       23958    50781465   83  Linux
/dev/sda4           23959       30401    51753397+  83  Linux

```
Hardy Heron is already installed on /dev/sda1, and obviously it's swap is sda2.   Any recommendations or good tutorials for a heron, xp, vista triple boot before I try this are appreciated :)

---

### Post by PmDematagoda on 2008-06-05
I do believe that Adobe CS3 works well in wine, so you can use that.

About partitioning, if you are going to change the partitions of Vista then you should use Vista's own partition manager for good measure since there have been threads about problems people get when partitioning Vista with the Ubuntu partitioner.

---

### Post by afbase on 2008-06-06
> **PmDematagoda said:**
> I do believe that Adobe CS3 works well in wine, so you can use that.


I've heard otherwise. But i'll take the windows partitioner advice in hand

---

### Post by PmDematagoda on 2008-06-06
> **afbase said:**
> I've heard otherwise. But i'll take the windows partitioner advice in hand

Did you try running Adobe CS3 on wine?

---

### Post by afbase on 2008-06-06
> **PmDematagoda said:**
> Did you try running Adobe CS3 on wine?

Well now that you've mentioned it, no I haven't.  I'll give it a shot, but if i run into problems, I'm gonna just try that windows boot method I thought of.  I'll keep the forum posted.

---

### Post by afbase on 2008-06-06
[http://ubuntuforums.org/showthread.php?t=469392](http://ubuntuforums.org/showthread.php?t=469392)

This isn't promising.

---

### Post by PmDematagoda on 2008-06-06
> **afbase said:**
> [http://ubuntuforums.org/showthread.php?t=469392](http://ubuntuforums.org/showthread.php?t=469392)

This isn't promising.

Yes, it doesn't, looks like you are better off dual booting.

---

### Post by afbase on 2008-06-06
Good news!

I have a triple boot of Vista, XP, and Ubuntu.  I had to start over and reinstall everything from scratch (good news was that i have everything backed up on my server).  

I started with installing XP.  Using the partition menu in the XP installation, I made 3 partitions: one for XP, Vista, and Ubuntu.  Once I loaded all the drivers for my hardware on XP, I moved on to the Vista installation.

I simply selected the manual setup (i don't recall the precise wording in the installation menu) in that menu, selected the second partition i had made from the XP installation.  Success.  

The tricky part...Ubuntu.

I booted from my live cd, and opted for manually partitioning the final partition i had made from my original partitioning in the XP installation.  I then made that partition into three partitions: the 'swap', a '/boot', and '/'.   the swap was about a gig, the boot was only 50 megabytes, and the remainder was left for the '/'.  The installation was a breeze and after restart I got a lovely menu!  A list of boots for a ubuntu and a 'vista/Longhorn boot'  that went to the vista menu that gives me the option to boot into vista or "earlier version of windows" (XP).

I followed the basic idea from this page: [http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/)

It worked like a charm. :popcorn:

---

### Post by Joeb454 on 2008-06-06
Triple booting XP, Vista & Ubuntu is incredibly easy (I have the same setup on this laptop).

As long as you install the OS's in that order (XP - Vista - Ubuntu) you can't go too far wrong.

Vista finds XP, and add's it as an option under the Vista boot loader - Grub finds Vista's bootload, and add's it to the Grub menu :)

---

### Post by chex_m8 on 2008-06-06
I'm still confused why you're even bothering to install vista in the first place. I guess some things are just inexplicable.

---

