---
title: "[Noob] Dual Install/Seperate HDDs/No boot selector"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Minigrue on 2010-10-25
Hello all,

I've done a fair amount of Googling and trawling the forum to see if this has been asked already but can find nothing.

I'm 'trying' to dual boot WinXP and Ubuntu 10.10 from 2 separate HDD's. Currently I'm on attempt number 6 but my patience wore thin about 2 days ago - here's the current state of play:

I have WinXP running fine (Was installed first) and I have Ubuntu running fine if I use a boot loader disc. I don't have any boot options at all - if I let the PC boot naturally then it just loads XP as normal.

I followed this guide to the letter: [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

(For those that don't want to read the link: It get's you to create 4 partitions on a drive - 1: ntfs for winxp (not touched) 2: Linux partition 3: linux-swap partition 4: fat32 osshare partition) THEN if you get no boot options, it creates an ubuntu.bin file which you move to the C:\ and edit the boot.ini to include it in the options)

But all the difference it makes is I get boot options, I press Ubuntu and my computer sits with a blinking cursor for as long as you let it.

I'm out of ideas, need help plz

Thanks in advance

---

### Post by kansasnoob on 2010-10-25
> **Minigrue said:**
> Hello all,

I've done a fair amount of Googling and trawling the forum to see if this has been asked already but can find nothing.

I'm 'trying' to dual boot WinXP and Ubuntu 10.10 from 2 separate HDD's. Currently I'm on attempt number 6 but my patience wore thin about 2 days ago - here's the current state of play:

I have WinXP running fine (Was installed first) and I have Ubuntu running fine if I use a boot loader disc. I don't have any boot options at all - if I let the PC boot naturally then it just loads XP as normal.

I followed this guide to the letter: [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

(For those that don't want to read the link: It get's you to create 4 partitions on a drive - 1: ntfs for winxp (not touched) 2: Linux partition 3: linux-swap partition 4: fat32 osshare partition) THEN if you get no boot options, it creates an ubuntu.bin file which you move to the C:\ and edit the boot.ini to include it in the options)

But all the difference it makes is I get boot options, I press Ubuntu and my computer sits with a blinking cursor for as long as you let it.

I'm out of ideas, need help plz

Thanks in advance

If you're fairly satisfied with your partitioning arrangement please use the Ubuntu Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will provide bootloader info and also a basic description of your current partition layout.

---

### Post by Minigrue on 2010-10-25
Hi kansasnoob,

Thanks for replying.

As it happens (Sod's law) whilst I was waiting on a reply I tried one final time to install and for some reason, this time it actually worked. I can't stress how annoying this has been added to the fact I did absolutely nothing different.

So finally I have a working dual boot with boot loader and can get into Linux without need of a bootCD.

Of course now I have different problems with some software I'm trying to install/configure but that's for a different thread.

Thanks for taking the time to help though - it's much appreciated.

mG

---

### Post by halj32 on 2010-10-25
a few years ago I remember trying for ages to get a dual boot system with 2HDD's to work in the end I found out that the only way I could get it to work was by installing grub on the primary HDD (windows) anything else wouldn't work

goodluck

---

