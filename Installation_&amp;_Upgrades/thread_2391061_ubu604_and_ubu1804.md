---
title: "ubu604 and ubu1804"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by robilio on 2018-05-05
Hello,
I've installed for testing ubu1804 in a separated partition of my pc and, from that moment on, my standard os ubu1604 does not boot any more...
ubu1804 does boot, and I can access the ubu1604 partition, but the boot process of ubu1604 hungs just after the grub, with a purple screen without any message.

disks configuration
I've got two disks: sda is a 128GB ssd, sdb is a 2TB hdd. sda is UEFI partitioned (sda1 is the boot partition), while sdb is standard.
Ubu1604 is in sda2 (root and home), and in sda3 there is a partition used for the virtual disk of win10 virtual machine.
sdb1 is a data partition; sdb2 is the partition dedicated to the test of various distros (in this case ubu1804!); sdb3 is the swap partition.

I think my error has been the installation of ubu1804 not in UEFI mode, as showed here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I've also tried to follow the guide on the same web page, but the problem is still there.... Here is the [boot-repair-log]("https://pastebin.com/W84K4T9E")
Before boot-repair I did try re-installing ubu18004 again in sdb2, but without success.

What can I do now? Formatting is not one of my preferred choice...

Thank you in advance to anyone will spend some time on my issue!
R.

---

### Post by Skaperen on 2018-05-05
i ran into this a long time ago.  whenever i want to make 2 disks independently bootable, i unplug the disk i am not installing to.  then when thie BIOS lets me select which to book from, it really loads only from the selected disk even though both as plugged in when booting.  lately, i needed to do a dual boot on a laptop where unplugging drives was not an option.  i had to take extreme care while installing but did succeed (so i have a bootable backup system on a 2nd drive and have a script to rsync everything from the 1st to 2nd.  i somtimes test boot the backup system.

practice by installing to USB memory sticks.  i have 9 of them, 8 GB each, just for this.  i need to do these in VMs for more fun.

---

### Post by robilio on 2018-05-06
Thank you!
But all I need is to recover my standard os ubu1604....
Anyone? 
R.

---

### Post by oldfred on 2018-05-06
It looks like if you have UEFI on, sda or 16.04 should boot.
Only issue I see is you have a mount in fstab of a second install, but that UUID does not exist.
It used to be that as long as / (root)'s UUID was correct it would just give a warning message and let you choose to boot if other UUIDs were not found. Not sure but have seen others not boot, or maybe timeout has be extended and no one waits that long.

From live installer mount your /etc/fstab in your sda2 and comment out your linux2 line.

Then with UEFI see if you can boot.

Since sda is gpt and uses UEFI, you really should only have gpt partitioning. But sdb is the now 35 year old MBR(msdos) partitioning.
You may be able to convert, but still need good backups. And with gpt you need either an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot.
       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by robilio on 2018-05-07
> **oldfred said:**
> It looks like if you have UEFI on, sda or 16.04 should boot.
Only issue I see is you have a mount in fstab of a second install, but that UUID does not exist.
It used to be that as long as / (root)'s UUID was correct it would just give a warning message and let you choose to boot if other UUIDs were not found. Not sure but have seen others not boot, or maybe timeout has be extended and no one waits that long.

From live installer mount your /etc/fstab in your sda2 and comment out your linux2 line.

Then with UEFI see if you can boot.
BINGO!
Awesome!!! You have solved my problem!!! Thank you a lot!

> **oldfred said:**
>  Since sda is gpt and uses UEFI, you really should only have gpt partitioning. But sdb is the now 35 year old MBR(msdos) partitioning.
You may be able to convert, but still need good backups. And with gpt you need either an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot.
       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Now I'm testing ubu1804, when I'll be ready to jump to the new LTS, I'll convert the 2nd disk to gpt (after a good backup, as you suggestion :) )

Thanks again for your precious help!
Apart from setting the [solved] tag on the subject, is there something that I can do to officially thank you for your support? Any click somewhere or similar? I'm new on this forum...

Bye,
R.

---

### Post by oldfred on 2018-05-07
Glad you got it working. :)

---

