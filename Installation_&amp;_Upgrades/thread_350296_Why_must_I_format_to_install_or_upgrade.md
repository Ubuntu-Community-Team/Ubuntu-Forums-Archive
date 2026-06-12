---
title: "Why must I format to install or upgrade?"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by jenks on 2007-01-31
Hello,

  I am trying to replace Fedora Core 6 with ubuntu edgy 6.10. Right now I have Windows XP in the first 10 GB partition, / in the second 69 GB partition and swap in the last 1 GB partition. I have about 45 GB of data in / that I want to keep, so I booted the ubuntu live CD, mounted my hard drive, created a /fedora directory and moved all other directories there, rebooted to the installer, and tried to manually partition, but the partitioner demands that I reformat /, even though the filesystem is already ext3 and there is plenty of space for the install. Why must the root partition be formatted? I don't want a separate /home partition. Unfortunately I don't have suitable network storage to store the data on. I suppose I could install to the first partition (and blow away XP :D) and then move my data in chunks while resizing the first and second partitions.
  I'm not even sure if this is the best place to post this. I would like to communicate directly with the team working on the ubuntu installer, but it wasn't obvious from ubuntu.com how to contact them. I bet a more direct feedback system for ubuntu would accelerate its development.

  Yours,

    Chris

---

### Post by jenks on 2007-01-31
Well, I decided to go with the plan above. I deleted the first 10GB partition containing XP and replaced it with an ext3 partition - but the "GNOME Partition Editor" wouldn't let me set any flags on the new sda1 partiton - the function was greyed out! I installed ubuntu to sda1 and tried to reboot, which didn't work of corse because the boot flag on sda1 was unset. So after booting back to the live CD, the partitioner (this time) let me set the boot flag. This time the boot worked, but was using the wrong (old) grub config on sda2, maybe because I changed hd0 to sda1 when the installer asked where to put the bootloader. In ubuntu I executed install-grub as root and now my system boots from the new config.
  Moving the data and repartitioning is a hassle because qtparted won't let me move the beginning of a partition, so I have to shrink sda2 to the size of the data, then create a new ext3 partition (sda4) with the leftover space, copy files from sda2 to sda4, and then shrink sda2 again and copy the rest to a new sda5 (after deleting the swap partition, since I ran out of partitions). Finally I should be able to delete sda2, expand sda1, and copy files from sda4 and sda5 to sda1, etc.
  I can't say this is the user-friendliest installation process I have gone through, considering all I wanted to do was switch from Fedora to ubuntu without deleting my 40GB mp3 library. I have about 5 years experience with Linux, so I can manage, but I would like to see the installer made a little more flexible for the sake of new Linux users.

  Yours,

    Chris

---

### Post by az on 2007-01-31
> **jenks said:**
>  moved all other directories there, rebooted to the installer, and tried to manually partition, but the partitioner demands that I reformat /, even though the filesystem is already ext3 and there is plenty of space for the install. Why must the root partition be formatted? 
    Chris

It doesn't.  Using the manual partitioning options, you need to pick *keep existing data* or something to the like.  There is no reason why a format is mandatory, and lots of reasons why someone would want to avoid this.

If you don't have that option, it's a bug.

---

### Post by jenks on 2007-02-01
I tried to reproduce the installation problem (of being forced to format the root partition), but was stopped by another bug - the installer wouldn't take the root partition I specified, saying I hadn't specified one (see the screen shot). I only have two partitions now - a 78 GB ext3 partition (sda1) and a 2 GB swap partition (sda2). The bug may have surfaced because I first tried to proceed with /media/sda1 specified as the mount point for sda1, so the error message was correct the first time. Then when I changed the mount point for sda1 to / and tried to proceed I continued to get the error (as shown). Backing up to the previous screen (the partitioner) and going forward again gave the same error. I would really like to see the installer work well, because it will determine the first impression of a lot of new Linux users. I would hate for them to get discouraged and install Vista instead!

  Yours,

    Chris

---

### Post by emarkay on 2007-02-01
I have wondered this to - the checkbox for the "/" and the "Swap" options is ALWAYS enabled and greyed out - at least in the " Dapper" installs.  While this may be a feature to insure a COMPLETE "virgin" install I think we should be allowed to disable formatting(presuming we know what we are doing)  this also ties into my post on "non-destructive" reloads: 
[http://ubuntuforums.org/showthread.php?t=344671](http://ubuntuforums.org/showthread.php?t=344671)

MRK

---

