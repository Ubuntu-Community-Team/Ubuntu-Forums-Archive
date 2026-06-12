---
title: "[SOLVED] Ubuntu 7.10 64-bit Install - SATA HD not showing?"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by BassKozz on 2008-02-16
**_System Spec's:_**
Abit IP35 Pro Mobo, Q6600 Proc, 4gb RAM, WD Raptor 150GB
I have only 1 partition on the raptor for approx 40GB for my WinXP, the rest of the drive is UNPARTITIONED and I planned on using my Ubuntu install to take the rest of the unused space for it's own.

I am attempting to install (Dual-Boot) Ubuntu 7.10 64-bit on my new rig which already has WinXP installed on it, but when I boot to the liveCD and click on the install icon, I get to step 4 and there is nothing showing in the partition manager, it's completely blank...
I assume Ubuntu isn't recognizing my SATA HD.

Is my motherboards chipset not supported?

PLEASE HELP,
Thanks,
-BassKozz

p.s. just ran "sudo fdisk -l" from the terminal and nothing came back (blank):
```
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 
``` :(

---

### Post by MasterJS on 2008-02-16
start up gparted on the live cd, and see if it sees it. Just type gparted in the terminal

---

### Post by BassKozz on 2008-02-16
Thanks for the suggestion MasterJS,
Tried "sudo gparted" from the terminal and "No devices detected" :(
Here is the output in the terminal window:
```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Unable to open /dev/fd0 - unrecognised disk label.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
```
I also rebooted using "nosplash" and I noticed the following lines during startup:
```
irq 19: nobody cared (try booting with "irqpoll" option)
Disabling IRQ #19
Buffer I/O Error on device fd0, Logical block 0
ata5.00:failed to set xfermode (err_mask=0x40)
Buffer I/O Error on device fd0, Logical block 0
Buffer I/O Error on device fd0, Logical block 0
ata5.00:failed to set xfermode (err_mask=0x40)
Buffer I/O Error on device fd0, Logical block 0
ata5.00:failed to set xfermode (err_mask=0x40)
```
Any idea's?

---

### Post by BassKozz on 2008-02-16
After a search on these forums for "Abit IP35" this is apparently a known issue, and there are a couple of threads discussing it:
[Install issue: initramfs failed to set xfermode]("http://ubuntuforums.org/showthread.php?t=637721")
[Abit IP35-E irqpoll boot option needed]("http://ubuntuforums.org/showthread.php?t=669741&highlight=abit+ip35")
[P35 Chipset Issues]("http://ubuntuforums.org/showthread.php?t=597252&highlight=abit+ip35")
And a Launchpad Bug Report:
[Bug #132776 in linux-source-2.6.22 (Ubuntu) / gutsy livecd fails in booting w/o irqpoll option on Abit IP35-Pro motherboard]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132776")

But I have yet to have found a definitive answer on how best to fix this problem?
Here are a few solutions that people have mentioned:
> [LIST]
[*]Unplug your SATA cables from SATA ports, Plug them into the highest numbered ports you have (i.e. from SATA 1/2 to SATA 5/6)
[*]Change BIOS settings on the SATA ports to AHCI from IDE"
[*]use irqpoll
[/LIST]

I don't know what's best to do here?

---

### Post by BassKozz on 2008-02-17
Ok I changed my SATA mode in my BIOS to AHCI, and rebooted to my XP Partition, wouldn't you know [BSOD]("http://en.wikipedia.org/wiki/Blue_Screen_of_Death") :(

So I now booted into the Ubuntu LiveCD w/ nospash option and the results:
```
Buffer I/O Error on device fd0, Logical block 0
Buffer I/O Error on device fd0, Logical block 0
Buffer I/O Error on device fd0, Logical block 0
Buffer I/O Error on device fd0, Logical block 0
```
Looks like irq19 error and ata5.00 xfermode errors have disappeared :)

ran "sudo fdisk -l"
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a423a42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5492    44114458+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```
Yea... Ubuntu see's my HD :D

Now how to fix the BSOD on the WinXP partition?
I guess I could manually switch back and forth in the BIOS (from ACHI to IDE), but what a pain in the ****.
Anyone know how to remedy?
Thanks,
-BassKozz

**_EDIT_**: Think I found a fix: [http://forums.pcper.com/showthread.php?t=444831]("http://forums.pcper.com/showthread.php?t=444831")
trying it now, will report back...
**_EDIT2_**: Everything works perfectly now thanks to the thread above :D

---

