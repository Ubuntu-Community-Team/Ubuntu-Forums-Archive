---
title: "MBR Crisis"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by Doctor Ninja on 2005-05-21
Well, I've installed Ubuntu many times before, and I love it. No other OS compares, and no other distro holds a candle. It is for this reason that, after an uphill installation battle, I decided that Solaris, no matter how long I spent getting it on my computer, had to go. I went to install Ubuntu, and now (after stage 1 installation) my hard drive isn't bootable. I've tried rewriting the MBR. I dual boot with Windows (for Ableton Live), and I've even tried using the XP disc as a rescue disc. No luck. Through all the installs of OS's that I've done, only BSD and Solaris have given me this much flak. The BSD fiasco wound up causing me to get a new hard drive. Any ideas? I can't afford a cop out solution again.

---

### Post by himuraken on 2005-05-22
Hey Ninja,
Please tell us more. Explain what size, type, and number of drives, and whether or not there is data on your main drive (I will assume c:\ or /dev/hda1). Please advise as to whether you have data or not.

---

### Post by mohaham on 2005-05-22
Did you choose the default partitioning option when installing...
The default option erases all data and partitions.

Did you install GRUB on MBR or on root..
GRUB should to be installed on the MBR to enable you to boot.

---

### Post by Doctor Ninja on 2005-05-23
Well, my partition table is relatively simple. I just have hda1, my NTFS partition, which I saved, wanting to retain my data there, and I have the end of the drive, the latter 10 GB of a 60 GB drive, dedicated to Linux. I installed GRUB to the MBR, formatting only the latter partition.

---

### Post by Doctor Ninja on 2005-05-23
[QUOTE=himuraken]Hey Ninja,
Please tell us more. Explain what size, type, and number of drives, and whether or not there is data on your main drive (I will assume c:\ or /dev/hda1). Please advise as to whether you have data or not.[/QUOTE]

My main drive is a laptop IDE drive, 60 GB, with hda1 as my NTFS Windows XP partition and hda2 as my ext3 Ubuntu partition. I did not format hda1 on install, I just reformatted hda2, my Solaris partition, and replaced it with the ext3 partition. I installed GRUB to the MBR.

---

