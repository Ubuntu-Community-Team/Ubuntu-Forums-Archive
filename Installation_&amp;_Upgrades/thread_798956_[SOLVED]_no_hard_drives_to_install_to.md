---
title: "[SOLVED] no hard drives to install to"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by talz13 on 2008-05-18
First, I have done a lot of searching, and have tried the "all-generic-ide" pci=nommconf, and irqpoll options on boot.

I tried hiren's bootcd this morning and everything in there could see my drive perfectly fine.  I went ahead and made an ext3 partition on the drive, but it still couldn't see it in the ubuntu installer, which leads be to believe it's just a problem with the linux distros that I've tried, and not an issue with the drive itself

Also tried openSUSE 10.3, same problem.

When I let it boot normally, it gives me errors of:```
ata3: port is slow to respond, please be patient (Status 0xd0)
```and GParted doesn't see the drive either, telling me:```
No devices detected
```I get an error message of ```
SRST failed (errorno=-16)
```when I try to boot with the additional boot options...


My system:
Asus A8V motherboard
120gb WD **P**ATA drive
nvidia 6800gt
2gb ddr400
athlon x2 4200+ s939

Tried:
ubuntu 8.04 amd64
ubuntu 8.04 32bit
ubuntu 8.04 32bit alternative
openSUSE 10.3 amd64

---

### Post by tamoneya on 2008-05-18
what does this command output:```
sudo fdisk -l
```

---

### Post by talz13 on 2008-05-18
> **tamoneya said:**
> what does this command output:```
sudo fdisk -l
```

Nothing, just returns to the prompt.

---

### Post by tamoneya on 2008-05-18
is your bios able to detect the drives?

---

### Post by chinobar on 2008-05-18
Had the exact same problem, bios saw the drives while the installation didn't.
The workaround was using all the 3 bootup commands you mentioned in the first post at the same time, at least i could see my drives then.
Now i'm stuck with Errno 5 :-P

---

### Post by Pumalite on 2008-05-18
[http://users.bigpond.net.au/hermanzone/p15.htm#5_](http://users.bigpond.net.au/hermanzone/p15.htm#5_)

---

### Post by talz13 on 2008-05-19
> **Pumalite said:**
>  [url]http://users .bigpond.net.au /hermanzone/p15.htm#5_[ /url]

I haven't gotten to the point where it will actually detect that there is a hard drive present yet.  fdisk doesn't show anything because there is nothing to show.  There are no disks labeled /dev/hdX or /dev/sdX.

I tried those thee commands before without success.  where do they need to be on the boot line?  I put them after the '--' at the end of the line.  I realize they have helped a number of people, but I'm not sure I it's the same situation as mine since they didn't seem to do anything.

Oh, and the drive is detected in the bios every boot, and has been recognized in various other programs like partition magic.

---

### Post by cdtech on 2008-05-19
my bad.

how about df -H

---

### Post by cdtech on 2008-05-19
> **chinobar said:**
> Had the exact same problem, bios saw the drives while the installation didn't.
The workaround was using all the 3 bootup commands you mentioned in the first post at the same time, at least i could see my drives then.
Now i'm stuck with Errno 5 :-P

What's Errno 5? :confused:

---

### Post by chinobar on 2008-05-19
> **cdtech said:**
> What's Errno 5? :confused:
[http://ubuntuforums.org/showthread.php?t=600126](http://ubuntuforums.org/showthread.php?t=600126) :)

---

### Post by VMC on 2008-05-19
If you boot up with a minicd (knoppix,puppy, slax, etc) and type the command 'fdisk -l' you should get some output showing partitions.

---

### Post by talz13 on 2008-05-19
> **VMC said:**
> If you boot up with a minicd (knoppix,puppy, slax, etc) and type the command 'fdisk -l' you should get some output showing partitions.

I'll try that tonight.  Hopefully something besides windows will detect my disks!

---

### Post by talz13 on 2008-05-20
I'm running knoppix 5.1 right now, and ```
sudo fdisk -l
``` produces ```
knoppix@Knoppix:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14593   117218241   83  Linux
``` so the drive is definitely there, just can't be seen by ubuntu or suse...

---

### Post by Pumalite on 2008-05-21
Go into BIOS and change the IDE Configuration until you hit the right one.

---

### Post by talz13 on 2008-05-21
> **Pumalite said:**
> Go into BIOS and change the IDE Configuration until you hit the right one.

I'm not sure what you mean by this, there aren't really any IDE settings to change.  Unless you mean defining the drive manually instead of auto (cylinders, heads, etc.)...

And still, why would everything except Ubuntu and suse be able to see it perfectly?

---

### Post by Pumalite on 2008-05-21
What BIOS and what motherboard do you have?

---

### Post by talz13 on 2008-05-21
> **talz13 said:**
> My system:
Asus A8V motherboard
120gb WD **P**ATA drive
nvidia 6800gt
2gb ddr400
athlon x2 4200+ s939

Bios 0219, nothing special about the new releases, but I might dig up a floppy drive to flash sometime if all else fails.

---

### Post by Pumalite on 2008-05-21
Are you able to access your BIOS? Can you tell me how is your hard drive configured?

---

### Post by talz13 on 2008-05-21
> **Pumalite said:**
> Are you able to access your BIOS? Can you tell me how is your hard drive configured?

Ok, every setting under the primary master is auto (type, LBA, block mode, pio mode, dma mode, smart monitoring) except for 32bit data transfer.

The configured settings shown above that are:
```
Device: Hard Disk
Vendor: WDC WD1200JB-00DUA3
Size: 120.0GB
LBA Mode: Supported
Block mode: 16 sectors
PIO Mode: 4
Async DMA: MultiWord DMA-
Ultra DMA: Ultra DMA-5
SMART Monitoring: Supported
```

---

### Post by Pumalite on 2008-05-21
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=332939](http://ubuntuforums.org/showthread.php?t=332939)

---

### Post by talz13 on 2008-05-23
I may have a solution that I'll have to try when I get home, but here it is:

I have a WD hard drive, and apparently they have different jumper settings from other drives.  The "Master" jumper that I *probably* have it on is the setting if you have a master AND A SLAVE drive attached on that channel.  Since I do not, it's causing problems.

I need to try switching it to "Master, single drive" or cable select and see if it solves my problem.

I will post back if this fixes my problem or not.

---

### Post by talz13 on 2008-05-23
Yahoo!  The jumper setting fixed my problem.  It WAS set on master, but apparently that was wrong.  Moved it to cable select and all my problems are gone!

---

