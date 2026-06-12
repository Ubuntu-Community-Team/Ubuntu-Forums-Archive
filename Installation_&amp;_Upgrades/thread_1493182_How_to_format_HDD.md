---
title: "How to format HDD"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by CinemaScope on 2010-05-25
I built a new computer and tried to install Ubuntu 10.4, but I could not get it to install (successfully installed on an older computer, so install disk was ok). I tried to install an earlier version: Ubuntu 9.10, which seemed to go well but ultimately failed during the progress bar stage. As  a last resort I bought windows 7, but when I try to install it, it cannot identify the drive formatting (presumably because of the half installed Ubuntu). Can anyone tell me how I can format a drive, with no operating system, so that Win 7 can be installed? Does win 7 still use NTSF?  Thanks.

---

### Post by F1R3H4CK3R on 2010-05-25
Win 7 does use NTFS and you can only format that drive if you have a CD that should have come with the computer to verify or modify computer's HDD. Or insert the ubuntu disk and format all partitions manually, then reboot and insert win7 disk, if any of this things don't work your HDD is dead. And Why you wanna install windows? Dude, Ubuntu/Kubuntu/Xubuntu/Lubuntu are better

---

### Post by CinemaScope on 2010-05-25
Thanks, I built the computer from scratch, there was no CD with the HDD. I've been using ubuntu for several years and wanted to use it on this machine, but I just can't get it installed. Now that I've spent £90 on Windows, I feel compelled to use it. If 10.4 had installed, I'd be on easy street by now! Don't worry, I'm typing this on a laptop with 9.10 - I keep the faith!

Can I use an Ubuntu live session to format the drive to NTFS? I might be able to get an earlier version of Ubuntu to run in order to perform that.

cheers.

---

### Post by F1R3H4CK3R on 2010-05-27
I think you can do it, actually I've never tried, but if you can format partitions from live cds you can format them as NTFS always in ubuntu.:)

---

### Post by bumanie on 2010-05-27
Download a gparted .iso and burn it to cd - the ubuntu cd does not have the ability to format to ntfs, that is left out of ubuntu's gparted version, as far as I remember. If you can't do that, from an ubuntu live cd, go to terminal and input this code > sudo mkfs.ntfs /dev/sda (or substitute the sda for your drive name - /dev/sdb or /dev/sdc etc). You could try the alternate cd for 10.04 - it often installs when the live cd won't, but I understand you spent (or some may say wasted) £90 already. ???Maybe a friend would buy it off you for a small loss????

---

### Post by srs5694 on 2010-05-28
*Do not* run mkfs.ntfs on /dev/sda, /dev/sdb, or /dev/sdc. That action will put NTFS on the *entire disk,* which will then be unpartitioned. Although this can work OK in some situations, it's likely to cause problems in other situations. You're better off to first create partitions (using fdisk, parted, GParted, or other tools) and then create filesystems on them (using mkfs.ntfs, parted, GParted, or other tools). Note that the partition creation and filesystem creation operations are one and the same in parted and GParted, or at least they can be one and the same.

---

