---
title: "livecd sends me to busybox (getting absolutely frustrated)"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by HangukMiguk on 2008-05-01
Every other LiveCD I have used (Ubuntu Dapper->Feisty) has worked perfectly fine. But using both Ubuntu Gutsy and Mint 4.0 has failed to work. Every time I try to load, I get sent to the busybox terminal. After removing the splash, I see errors with fd0. Here's what I've tried so far:

the modprobe piix option in busybox ("piix not found")
removing "quiet --splash" and adding "all generic_ide irqpoll"
disabling my floppy in BIOS (which I never use anyway), both with normal boot options, and with "all generic_ide irqpoll"

All give me the same problems.

I'm absolutely frustrated. I'm trying to get away from Ubuntu Hardy, and am now starting to think it wasn't so bad after all (After having MASS problems with BSD, then being unable to boot into LiveCD on either Ubuntu Gutsy or Mint 4.0).

Someone PLEASE help me.

---

### Post by daimaru on 2008-05-01
> **HangukMiguk said:**
> I'm absolutely frustrated. I'm trying to get away from Ubuntu Hardy, and am now starting to think it wasn't so bad after all ...Someone PLEASE help me.
What exactly are you trying ??? installing ubuntu getting away from it :confused:
If you're installing why not use the alternate cd, but i guess you are trying to just run ubuntu from live cd, not install it? is that right?  And if so are you trying to run hardy or gutsy or mint or what ?

---

### Post by HangukMiguk on 2008-05-01
I'm trying to install.  OMG, I don't have any more blank CDs, I cannot get the install CD.

All I want is to boot into LiveCD and/or install Ubuntu Gutsy or Mint.  I don't care which right now, I just want to get something installed.

---

### Post by daimaru on 2008-05-01
> **HangukMiguk said:**
> I'm trying to install.  OMG, I don't have any more blank CDs, I cannot get the install CD.
Damn no more cd's ... that sucks. I had trouble once with i think it was feisty live cd so i used the alternate cd and was able to install without problems. just had to fix my xserver before i was able to boot into gfx mode. I guess the best choice would be to get a new cd :) burn alternate on it and then install from that. 

after install, if its a graphic card issue you might have problems with the xserver, but that can be fixed. But it might be good to know what your running (gfx wise, laptop model | desktop?) so people can help you out. if it does not work out of the box style.

---

### Post by HangukMiguk on 2008-05-01
> **daimaru said:**
> Damn no more cd's ... that sucks. I had trouble once with i think it was feisty live cd so i used the alternate cd and was able to install without problems. just had to fix my xserver before i was able to boot into gfx mode. I guess the best choice would be to get a new cd :) burn alternate on it and then install from that. 

after install, if its a graphic card issue you might have problems with the xserver, but that can be fixed. But it might be good to know what your running (gfx wise, laptop model | desktop?) so people can help you out. if it does not work out of the box style.
I'm positive it's not GFX problems, it's a problem with my Floppy Drive I'm assuming.  Plus, I've never had problem with any distro running X before, my GFX card is just a generic nvidia card, which worked before on Dapper->Hardy

---

### Post by debil on 2008-05-01
I'm with daimaru on this. You should try installing with the alternate CD. It has more options to choose from. For some reason GRUB won't work on my system, so I'm using LILO as my bootloader. "Had to" install from the alternate CD because of that.

---

### Post by HangukMiguk on 2008-05-01
> **debil said:**
> I'm with daimaru on this. You should try installing with the alternate CD. It has more options to choose from. For some reason GRUB won't work on my system, so I'm using LILO as my bootloader. "Had to" install from the alternate CD because of that.
I just found a blank, and am downloading now.

Is there a guide I need to look at before installing, or is it pretty straightforward?

-OR-

Is it going to be semi-command based like a Gentoo install or is it ncurses based?

---

### Post by debil on 2008-05-01
I think it's ncurses based and it is quite straightforward. No guide necessary I think.

---

### Post by daimaru on 2008-05-01
only part you have to pay attention to is the partitioning. either use manual if you already have partitions set up (make sure you know which partitions you are going to use. if you only have windows as a dual boot you'll see its partition displayed as ntfs so you really cant go wrong there), or if you're going to use the whole HD its even easier just let the installer do its stuff by choosing use whole hd or something like that. - really can't remember. I always use manual partition to be on the safe side and since I'm tripple booting.

---

### Post by tofuconfetti on 2008-05-01
Read through this thread.  You'll find the answer you're looking for.

[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

Look near the last of the thread.  There are some parameters you may need to pass to the kernel boot line.

---

