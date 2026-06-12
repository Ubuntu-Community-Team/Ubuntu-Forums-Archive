---
title: "How to make hda2 bootable during installation?"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by usrloco on 2006-07-30
There must be an obvious answer to this, but I cannot find it:

I am trying to install Ubuntu on my laptop, dual booting XP. I had a previous installation of Fedora Core on this machine, so the partitions are already as I want them. In particular, there is a /home partition (on hda5) that I very much want to preserve.

I want hda2 to be /

Much of what I have read about dual booting Ubuntu strongly recommends _not_ installing GRUB to the MBR, and indeed when I first did the dual boot thing almost a year ago I got into trouble doing exactly that and had to reinstall windows, and start over. At that time I was able to get fedora to put the bootloader on hda2, and that worked. That's what I am trying to do this time around, as well.

When I get to the manual partition section of the Ubuntu installer. it shows me /hda1 (windows) as bootable, but not hda2. I have looked everywhere on the screen in an attempt to set the bootable flag on hda2, but cannot find a way to do it. I actually started typing "boot" and a nice little text field appeared at the bottom of the flags column. I thought "Aha! Got it!", but when I pressed return and the field went away hda2 was still not listed as bootable. 

Can anyone tell me how to make a partition bootable in the installer's partitioning tool? (Or confirm that it is not in fact possible.)

---

### Post by Iandefor on 2006-07-30
I believe you need to open up GParted before running the installation- the setting should be in there.

---

### Post by usrloco on 2006-07-31
Thank you, Iandefor. That was the answer. I guess because I knew I already had the partitions set up the way I wanted them I skimmed the Partitioning section of the install instructions. (Will he never learn?) 

Now as memory comes slowly leaking back to me I remember having to open partitioners a couple times during the previous fedora install to switch the active partition to hda2 (linux) then back to hda1 (since I wound up having to use the XP bootloader in the end).

Ubuntu works fine booting both Linux and Windows on my HP laptop, so this time I can just leave hda2 as the active partition.

---

### Post by az on 2006-07-31
There are only a few special cases where you would want to not overwrite your MBR.  For the most part, it is the best thing to do to dual boot.

I don't know where you got them impression that it was a bad thing.

---

