---
title: "Unable to edit partitions during setup (9.10 x64)"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by jmpires on 2010-01-24
I can't edit the partitions in the install setup: I see a hard disk (sda) with no partitions or user devices, and 2 RAID devices

The behavior of OpenSuse 11.2 x64 installation is much alike.

I have googled with every keyword combination I remembered, but I can't find anything that gives me a clue to what may be happening.

I have already tried the 3 SATA configurations (the IDE that works with the installed Win 7, AHCI and RAID), but the result is always the same. Now the strangest thing is that in OpenSuse, fdisk and parted correctly identify the partitions. As far as I remember, parted isn't able to do modifications and fdisk says that the boundaries of the first, tiny partition, doesn't match the number of cylinders (or something like it). However, I was able create a partition with fdisk on the empty space and format it, delete it again and repeat the process a couple of times with no errors. The partituions are signed as msdos.

GParted from Ubuntu also shows the partitions, but I didn't try to do any modifications, namely because I don't think that it can solve my problem and I don't want to risk installing windows again.

The hardware is brand new, a Asus M4A785Td-V Evo with an Amd Phenom II X4 965 and a WDC-WD5000ACCS-0 500 Gb HD. My lazyness made me asking the guys from whom I bought it to install Win7 Ultimate 64 in a NTFS partition, leaving half the disk untouched. They assure me that it is a &quot;plain vanilla&quot; (&quot;next, next, next&quot;) installation . I guess I could try to see if I could do the partition setup in the &quot;RAID&quot; part of the Expert partitioner, but I have strong doubts that it solves the problem and it would be quite boring to conclude that I ruined the windows installation for nothing.

Could it be any awkward problem specific of the motherboard / SATA controller or its drivers?

Any input is welcome.
Regards, Jose

---

### Post by darkod on 2010-01-24
So, you are NOT running raid but ubuntu can see the drives as belonging to raid right?

If that is correct, ubuntu 9.10 can detect remains of raid settings on the drives. In this case do:
First go into BIOS and make sure you don't have any raid settings enabled.
Then boot with ubuntu cd, Try Ubuntu option, and in terminal do:

sudo dmraid -E -r /dev/sda (also for /dev/sdb if you have another disk and you want to remove the settings too)
sudo apt-get remove dmraid

That should ger rid of the raid settings for you. Reboot and start the install process and see how it goes.

---

### Post by jmpires on 2010-01-24
> **darkod said:**
> So, you are NOT running raid but ubuntu can see the drives as belonging to raid right?

If that is correct, ubuntu 9.10 can detect remains of raid settings on the drives. In this case do:
First go into BIOS and make sure you don't have any raid settings enabled.
Then boot with ubuntu cd, Try Ubuntu option, and in terminal do:

sudo dmraid -E -r /dev/sda (also for /dev/sdb if you have another disk and you want to remove the settings too)
sudo apt-get remove dmraid

That should ger rid of the raid settings for you. Reboot and start the install process and see how it goes.

Thank's for the tip. If it wasn't so late in the night I'd try it right now. What do you think about the risk of  the procedure breaking the windows 7 installation? Just to be "menthaly prepared" - one thing is having an accident and another one is knowing in advance the annoyance is inevitable. :)
Regards, José

---

### Post by 73ckn797 on 2010-01-24
I am not familiar with raid setups.

I will recommend a good search tool at [http://www.uboontu.com](http://www.uboontu.com)

It will find anything Ubuntu/Linux you want to find.

---

### Post by jmpires on 2010-02-01
> **darkod said:**
> So, you are NOT running raid but ubuntu can see the drives as belonging to raid right?

If that is correct, ubuntu 9.10 can detect remains of raid settings on the drives. In this case do:
First go into BIOS and make sure you don't have any raid settings enabled.
Then boot with ubuntu cd, Try Ubuntu option, and in terminal do:

sudo dmraid -E -r /dev/sda (also for /dev/sdb if you have another disk and you want to remove the settings too)
sudo apt-get remove dmraid

That should ger rid of the raid settings for you. Reboot and start the install process and see how it goes.

**IT WORKED!** Thank you very much. And it didn't break the Win7 installation.  Just wondering: the 'nodmraid' option shouldn't do the same? I tried with no success, the installation hanged.

---

