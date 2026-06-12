---
title: "Re-Installing Ubuntu Partition Help Needed"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by hiflyact on 2007-11-11
Hello,

I am re-installing Ubuntu due to the OS getting hosed up and I could not repair it.  I had it dual booting with XP.  I re-wrote the MBR and was able to delete the ext and linux swap partitions using Gparted, but I am having problems getting rid of the unallocated space along with the extended partition.

Here's what the display looks like for me.  I need to add the unallocated space to /dev/hda2 and then either delete the /dev/hda3 partition or move that space to /dev/hda2 also.  I don't need the /dev/hda3 partition any more.  How can I do this within GParted?  

Thank You.

Partition     File Sys             Size              Used           Unused      Flag
=====     =====          ====       ======     =====     ===
/dev/hda2     ntfs             45.29GiB     25.32 GiB     19.97GiB     boot
/dev/hda3    extended     24.55GiB        -  -                 - -             lba
unallocated  unallocated  22.55GiB         -  -                 - -

---

### Post by forestpixie on 2007-11-11
you should be able to delete hda3 in gparted and then grow hda2 to take up the slack.

you say you're reinstalling ubuntu - where are you going to be installing it?

---

### Post by hiflyact on 2007-11-11
I was able to get rid of the linux-swap and the ext partition fine, but not the extended one.  I believe all 3 were created when I installed Ubuntu, since my entire C: was all on one partition before the install.

I just want to put the drive back the way it was and then re-install Ubuntu.  When I installed the first time, I let the wizard do an auto-config, basically took the some of the free space on C: and installed Ubuntu there.  I'm guessing that it was on it's own partition.

I think /dev/sda5 might have been created by Ubuntu as it appears to be part of the extended partition (see image).

[[IMG]http://aycu37.webshots.com/image/32716/2003822315311533752_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2003822315311533752)

---

### Post by forestpixie on 2007-11-11
my poor old eyes can't see that :) can you get a scrnshot from the live cd - it should have gparted there -

---

