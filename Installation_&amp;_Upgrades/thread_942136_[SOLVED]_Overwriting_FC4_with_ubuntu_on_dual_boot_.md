---
title: "[SOLVED] Overwriting FC4 with ubuntu on dual boot laptop.. Grub questions/concerns"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by al_mckin on 2008-10-08
Hi everyone,

As I mentioned in this thread [http://ubuntuforums.org/showthread.php?t=940802]("http://ubuntuforums.org/showthread.php?t=940802"), I am trying to install ubuntu over an existing FC4 installation, on a dual boot FC4/XP laptop.

The complication is, I cant boot from CD.  So I decided to create a new partition to put the install image in, and use grub to boot it and then overwrite my FC4 install.

So I added my new partition, and when I rebooted my laptop, I got the grub stage 1 prompt.  I was able to boot by manually entering the grub config entries.

I guess this happened because my FC4 install had /boot on the root partition on hd0,5 which changed to hd0,6.

So my question is, does grub stage 1 need to know some info about where stage 2 is?  If so, can I fix it?

I think Ubuntu does something different with grub than FC4 did, is this right?  I saw somewhere that grub stage 1.5 goes after the MBR.  On my laptop, xp is currently on the first partition.  Will this cause me any problems if I install ubuntu over the existing FC4?

My partition table currently looks like this (I'm not sure about the exact numbering this is in position on disk order)

0: XP (primary)
1: FAT 32 shared (primary)
2: (extended)
  3: linux swap (logical)
  4: new FAT 32 partition for ubuntu install image (logical)
  5: old FC4 with /boot on it (logical)
6: FAT 32 rescue partition (primary)

Will I be ok to install ubuntu on partition 5? Do I need to do anything special with grub?

---

### Post by al_mckin on 2008-10-10
Ok I got this to work.

I used the instructions here [https://help.ubuntu.com/community/Installation/FromLinux?highlight=(installation)]("https://help.ubuntu.com/community/Installation/FromLinux?highlight=(installation)") with the LiveCD.

The only slight problem I had was when I created the new partition, grub didnt know where its stage 2 was at was stuck at the grub> prompt.

I tried this first of all with Intrepid Beta, which did not work as of yesterday.  The installer complained about not being able to umount one of the filesystems and caused a funny reboot of X one other time.

The above method worked with the Hardy 8.04.1 live cd and reinstalling grub worked without any problems.

---

