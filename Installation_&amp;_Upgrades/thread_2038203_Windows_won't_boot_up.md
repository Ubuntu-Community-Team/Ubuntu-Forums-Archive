---
title: "Windows won't boot up"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by robertgjerdrum on 2012-08-06
Hey. About a week ago, i did a full installation of ubuntu 12.04. No dual boot or something, i only have ubuntu on my computer. But i want windows back, but when i put the windows installation CD in the CD-ROM and try to boot it up, it doesnt work! nothings happening! I have made a partition witch has the file system "NTFS" but the windows installation cd wont but on that partition either. The problem is that i have ubuntu 12.04 as my main OS, so my main partition is ext3/ext4, and the windows installation cd automaticly tries to boot up on that partition instead of the NTFS partition. please help????

---

### Post by deadflowr on 2012-08-06
Have you tried setting your system to boot from CD? If you're booting into the Ubuntu partition, then you most likely have your hard drive set as the higher boot option in the boot sequence.
Somewhere during the initial power up of your system, usually on the screen somewhere, it will say the name of a button and boot menu or something like that(it differs from system to system) it most likely will also say the name of a button and setup or something like that(this usually means the bios setup menu)this will be at the beginning of turning the system on, and it usually is very quick. Try to read what comes across the screen to find out.

And as a side note you can never boot from an empty partition, like your Ntfs partition.

OR, the windows installation disk has gone bad and is itself unbootable.

---

### Post by darkod on 2012-08-06
As already mentioned make sure you are booting from the cd-rom, not the hdd. When you boot from the cd it doesn't matter what partitions you have on the hdd, whether windows, linux, etc. You are not booting from the cd-rom, and you should be.

---

### Post by robertgjerdrum on 2012-08-07
I am booting from the cd-rom, but still nothing happens

---

### Post by oldfred on 2012-08-07
Windows installs to the primary partition that is formated NTFS with the boot flag. If it is trying to install to sda1, then you probably still have the boot flag on the Linux partition. Grub does not use boot flag, but Windows has to have it.

Post this:

sudo fdisk -lu

---

### Post by darkod on 2012-08-08
> **robertgjerdrum said:**
> I am booting from the cd-rom, but still nothing happens

In that case either your cd-rom or the windows media is broken. You said "windows cd tries to boot on that partition", which makes no sense.

CD/DVD installation media boots from the cd/dvd, not from any partitions. In rare cases, what type of partitions you have on the hdd might influence the cd boot, but very rarely. In general, it doesn't care because first the install process should start booting from the cd, and the installer offers you to create partitions for windows on your hdd. That's why it shouldn't care what partitions you have or not, it will offer you to make ntfs partition for windows.

Imagine you just installed brand new hdd. It doesn't have any partitions on it. The windows cd should still boot and you can create partitions with the installer, right?

Focus on the cd-rom and the windows cd. The probability is low for this to be issue with the partitions on the hdd.

---

