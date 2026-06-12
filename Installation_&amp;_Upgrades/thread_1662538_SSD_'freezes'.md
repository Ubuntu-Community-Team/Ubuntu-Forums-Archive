---
title: "SSD 'freezes'"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by Xeli on 2011-01-08
Hello, i've recently(month-month and a half) build new a computer (details listed below)

And under both windows and linux my ssd card seems very unstable. After some firmware updates and driver fixed windows does not bsod anymore but sometimes hangs. On Linux however i ofter find the following in 'dmesg':

```
[ 7543.367938] ata7.00: status: { DRDY }
[ 7543.367985] ata7.00: failed command: WRITE FPDMA QUEUED
[ 7543.368038] ata7.00: cmd 61/18:18:98:f4:5a/00:00:03:00:00/40 tag 3 ncq 12288 out
[ 7543.368040]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 7543.368166] ata7.00: status: { DRDY }
[ 7543.368216] ata7: hard resetting link
[ 7543.912167] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 370)
[ 7543.912808] ata7.00: configured for UDMA/100
[ 7543.912814] ata7.00: device reported invalid CHS sector 0
[ 7543.912819] ata7.00: device reported invalid CHS sector 0
[ 7543.912829] ata7: EH complete
[ 7568.775726] lo: Disabled Privacy Extensions
[ 7568.871714] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro,commit=0
[12724.141678] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x6 frozen
[12724.141685] ata7: SError: { 10B8B Dispar }
[12724.141688] ata7.00: failed command: FLUSH CACHE
[12724.141696] ata7.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[12724.141697]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[12724.141701] ata7.00: status: { DRDY }
[12724.141706] ata7: hard resetting link
[12724.689309] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 370)
[12724.690054] ata7.00: configured for UDMA/100
[12724.690059] ata7.00: retrying FLUSH 0xe7 Emask 0x4
[12724.692961] ata7.00: device reported invalid CHS sector 0
[12724.692969] ata7: EH complete
[33802.071030] ata7.00: exception Emask 0x0 SAct 0x3ff SErr 0x180000 action 0x6 frozen
[33802.071037] ata7: SError: { 10B8B Dispar }
[33802.071041] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071049] ata7.00: cmd 61/08:00:10:48:0d/00:00:04:00:00/40 tag 0 ncq 4096 out
[33802.071051]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071054] ata7.00: status: { DRDY }
[33802.071057] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071065] ata7.00: cmd 61/08:08:28:48:4d/00:00:03:00:00/40 tag 1 ncq 4096 out
[33802.071066]          res 40/00:14:48:95:41/00:00:03:00:00/40 Emask 0x4 (timeout)
[33802.071070] ata7.00: status: { DRDY }
[33802.071073] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071080] ata7.00: cmd 61/08:10:90:48:8d/00:00:03:00:00/40 tag 2 ncq 4096 out
[33802.071082]          res 40/00:14:48:95:41/00:00:03:00:00/40 Emask 0x4 (timeout)
[33802.071085] ata7.00: status: { DRDY }
[33802.071088] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071095] ata7.00: cmd 61/08:18:e0:5e:8d/00:00:03:00:00/40 tag 3 ncq 4096 out
[33802.071097]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071100] ata7.00: status: { DRDY }
[33802.071103] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071110] ata7.00: cmd 61/10:20:00:6d:8d/00:00:03:00:00/40 tag 4 ncq 8192 out
[33802.071112]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071115] ata7.00: status: { DRDY }
[33802.071118] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071125] ata7.00: cmd 61/08:28:b0:86:8e/00:00:03:00:00/40 tag 5 ncq 4096 out
[33802.071126]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071130] ata7.00: status: { DRDY }
[33802.071133] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071140] ata7.00: cmd 61/08:30:60:57:cd/00:00:03:00:00/40 tag 6 ncq 4096 out
[33802.071141]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071145] ata7.00: status: { DRDY }
[33802.071148] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071155] ata7.00: cmd 61/08:38:10:5c:cd/00:00:03:00:00/40 tag 7 ncq 4096 out
[33802.071156]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071160] ata7.00: status: { DRDY }
[33802.071163] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071170] ata7.00: cmd 61/08:40:70:72:4d/00:00:04:00:00/40 tag 8 ncq 4096 out
[33802.071171]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071175] ata7.00: status: { DRDY }
[33802.071178] ata7.00: failed command: WRITE FPDMA QUEUED
[33802.071184] ata7.00: cmd 61/08:48:38:81:5c/00:00:03:00:00/40 tag 9 ncq 4096 out
[33802.071186]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[33802.071190] ata7.00: status: { DRDY }
[33802.071195] ata7: hard resetting link
[33802.617156] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 370)
[33802.617928] ata7.00: configured for UDMA/100
[33802.617935] ata7.00: device reported invalid CHS sector 0
[33802.617939] ata7.00: device reported invalid CHS sector 0
[33802.617942] ata7.00: device reported invalid CHS sector 0
[33802.617945] ata7.00: device reported invalid CHS sector 0
[33802.617948] ata7.00: device reported invalid CHS sector 0
[33802.617950] ata7.00: device reported invalid CHS sector 0
[33802.617953] ata7.00: device reported invalid CHS sector 0
[33802.617956] ata7.00: device reported invalid CHS sector 0
[33802.617971] ata7: EH complete
[40654.136797] ata7.00: exception Emask 0x0 SAct 0x6 SErr 0x180000 action 0x6 frozen
[40654.136804] ata7: SError: { 10B8B Dispar }
[40654.136808] ata7.00: failed command: WRITE FPDMA QUEUED
[40654.136816] ata7.00: cmd 61/10:08:70:68:6f/00:00:03:00:00/40 tag 1 ncq 8192 out
[40654.136818]          res 40/00:14:48:95:41/00:00:03:00:00/40 Emask 0x4 (timeout)
[40654.136821] ata7.00: status: { DRDY }
[40654.136825] ata7.00: failed command: WRITE FPDMA QUEUED
[40654.136832] ata7.00: cmd 61/08:10:30:82:5c/00:00:03:00:00/40 tag 2 ncq 4096 out
[40654.136833]          res 40/00:14:48:95:41/00:00:03:00:00/40 Emask 0x4 (timeout)
[40654.136837] ata7.00: status: { DRDY }
[40654.136843] ata7: hard resetting link
[40654.685280] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 370)
[40654.685922] ata7.00: configured for UDMA/100
[40654.685934] ata7: EH complete

```

And when it actually 'crashes' it's just the ssd which is frozen (downloads with go to another hdd continue for example) i get some other but similar error, next time i'll write it down and post it here.

I have no idea if it's the motherboard or the ssd, it does not seems to be de sata3 card cause if i connect the ssd directly to a sata2 port on the motherboard i get the same freezes.

Could anyone provide me with pointers how to find the problem?

SSD crucial C300 64gb - connected via an marvell sata3 pci card - AHCI
Asrock p55 deluxe
nvidia gts 450 
intel core i5 -  760
Kubuntu 10.10

---

### Post by efflandt on 2011-01-08
That definitely is abnormal.  I originally installed Maverick on my Intel SSD with the drive installed in my laptop (limited by sata1) and then moved the drive to my desktop (twice as fast on sata2).  And it has been running Natty since alpha1 on ext4 with journal disabled without any drive issues in either OS.  It is mounted with **noatime** and **discard** (for TRIM) options, using tmpfs for /tmp and no swap.

I don't know if it matters that I am using deadline (instead of default cfq) as its scheduler and single fifo, with following in /etc/rc.local

```
echo deadline > /sys/block/sdb/queue/scheduler
echo 1 > /sys/block/sdb/queue/iosched/fifo_batch
```dmesg is clean

```
efflandt@natty-ssd:~$ **dmesg | grep ata2**
[    1.396266] ata2: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4180 irq 40
[    2.491942] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.492324] ata2.00: ATA-7: INTEL SSDSA2M080G2GC, 2CV102HD, max UDMA/133
[    2.492329] ata2.00: 156301488 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    2.492726] ata2.00: configured for UDMA/133
```My hardware is similar to, but a bit under yours.  Curious that yours says UDMA/100 (mine only does that for DVD/CD drive).  Are your SATA and power cables tight?  Have you tried the SSD on another computer?

---

### Post by SamTzu on 2011-01-10
Same problem with Ubuntu 10.10 server 64bit installed on CompactFlash disk.
I put EXT2 / on Flash and /var on LVM2 formatted sata disk.

ata3.00: failed command: WRITE FPDMA QUEUED

Related to this..?
[https://bugs.launchpad.net/ubuntu/+bug/550559](https://bugs.launchpad.net/ubuntu/+bug/550559)

---

### Post by aix1 on 2011-01-27
I am experiencing what looks like exactly the same problem. I have a Crucial SSD drive (M225) on a P55 motherboard. I've tried several ports on the Intel SATA controller (haven't tried the Marvel yet), three M225 drives and two SATA cables, to no avail. Trying to write a couple of gigabytes to the drive gives problems almost identical to what you describe (the only difference is that the SATA command that fails varies).

I'm running 64-bit Ubuntu 10.10.

Full report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/707583?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/707583?comments=all")

Please feel free to add your observations to the Launchpad ticket and/or post them here (especially if you manage to find a configuration that works.)

---

### Post by aix1 on 2011-01-27
> **SamTzu said:**
> Same problem with Ubuntu 10.10 server 64bit installed on CompactFlash disk.
I put EXT2 / on Flash and /var on LVM2 formatted sata disk.

ata3.00: failed command: WRITE FPDMA QUEUED

@SamTzu - what motherboard/chipset is the drive connected to?

---

### Post by Bas232 on 2011-02-19
I have the same issue.
I tested 2 SSD's.
One OCZ Vertex2, that wouldn't run at all, unless Ubunu 9.10 is used.
One Intel X25, runs but when pushed it locks, but does run 10.04LTS.
Chipset is MSI MediaLive, nVidia MCP chipset.
Strangely, WindowsXP works without problems, as does Ubuntu 9.xx or earlier.

---

### Post by aix1 on 2011-02-19
Having experimented with:

[LIST]
[*]three different SSD drives (same make/model);
[*]two different SATA cable;
[*]two different SATA ports;
[*]latest Crucial firmware;
[*]turning various things on and off in the BIOS,
[/LIST]

I've given up and have bought a standard HDD. This works like a charm. No issues whatsoever. As an added bonus, sleep issues I was having with box but couldn't quite figure out are also gone.

---

### Post by Bas232 on 2011-02-21
I'm running for a day now without freeze.
I added the kernel parameter libata.force=noncq after quiet splash.
Either it's working or it's because I still run 9.10, however 9.10 messed up the other day too, so bad it wouldn't boot anymore.
Give it a shot, it may just be NCQ messing on SSD's.

---

### Post by aix1 on 2011-02-21
> **Bas232 said:**
> I'm running for a day now without freeze.
I added the kernel parameter libata.force=noncq after quiet splash.
Either it's working or it's because I still run 9.10, however 9.10 messed up the other day too, so bad it wouldn't boot anymore.
Give it a shot, it may just be NCQ messing on SSD's.
Great stuff. It's a bit difficult for me try this right now, but please keep us posted!

---

### Post by Bas232 on 2011-02-21
Well I do run on an Intel X25 80GB SSD now.
As the Vertex would install one bit, however, I never tested the Vertex with the kernel parameter, as I didn't even get it to boot (liveCD would crach too when access the SSD).
The Intel went further, but crash a few hours after the install.

There is a whole lot what can be tried :P

[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

But so far this one looked the best to fit the problem.
BTW, I tried all BIOS parameters, upto PIO mode, but nothing worked.
So I decided to look at the kernel, as that is the next logical step if the BIOS doesn't solve anything.

---

### Post by aix1 on 2011-02-21
Bas232, out of interest, what chipset is your motherboard based on?

---

### Post by Bas232 on 2011-02-21
MSI MediaLive nVidia MCP51 (well according to flashrom).

I checked with OCZ about the Vertex, but they couldn't say more then it should work with AMD chipset, and to check with MSI :roll:
So I talked to MSI and they told me nVidia isn't SSD verified by Intel SSD.

As Windows XP runs fine on either SSD, Vertex or Intel X25, I'm suspecting the Kernel has something to do with it or the ATA drivers.

The ncq is a longshot, but somebody else mentioned it a long time ago too, so I figured why not? :P
So far 9.10 (with all updates, but no version upgrade) works fine and no hickups or anything.

And yes, I have /var /tmp /home and swap stored on a normal harddisk, not on the SSD.

---

### Post by aix1 on 2011-02-21
Interesting... mine is a totally different chipset (Intel P55). Also, I didn't try Ubuntu 9.x, only 10.10.

How do you test the system for stability? When I was actively experimenting with this, I found that doing a flat-out multi-gigabyte write onto the disk (for example, using "dd") would consistently trigger the fault.

---

### Post by Bas232 on 2011-02-21
That is one way.
I did a lot of installing and/or running W7 in a Virtual-box will trigger it too.
Simply put; create a lot of I/O on the SSD and it locks.

It could well be NCQ, as using NCQ on an SSD is simply stupid.
NCQ tries to order the read/write command in such a way that the heads of a HARDDISK don't need to wait rotations to read/write data.
But as an SSD doesn't have heads, nor does it spin; it access the data straight away without waiting, as such NCQ is unneeded and unwanted when you use an SSD.

My idea was that NCQ tried to rearrange the commands properly for a harddisk, but the kernel gets confused as to why the SSD delivers the data in the wrong order (or too fast).

So I believe the SSD / controller simply locks due to wrong communications.

I could be totally wrong, time will tell, but that is my idea behind it.
I believe an SSD doesn't know NCQ or is too fast for Linux to do NCQ.

If it didn't crash with this kernel:

> 
bas@workstation:~$ uname -r
2.6.31-22-generic


Then I will upgrade to 10.04LTS tomorrow and do more testing.
But I doubt it matters what version you run, I think it's a kernel/driver matter as 9.10 crashed the other day real hard.

And for others, no it's not the computer going wrong, as it does Linux/Windows fine from harddisk.
But kept crashing on 3 different SSD's, until now _CROSSING MY FINGERS SO HARD THEY START TURNING PURLE_:lolflag:

---

### Post by Bas232 on 2011-02-22
Still running fine, no hickups or crashes.
Aix1, did you test the kernel param on your machine already?

---

### Post by aix1 on 2011-02-23
> **Bas232 said:**
> Still running fine, no hickups or crashes.
Aix1, did you test the kernel param on your machine already?
I no longer have any SSD drives in the machine so testing this would be a mini-project in its own right (one for which I sadly lack time at the moment.)

---

### Post by allbread on 2011-02-26
I am running into what seems like a similar issue, I am attempting to install Ubuntu 10.10 (64-bit) on a Crucial 256GB SSD.   Currently I have a working install of Ubuntu running on the board off   of a spare Hitachi 250GB drive however I ultimately want my primary  boot  partition on the SSD for performance reasons. 

Tyan Thunder S2915-E
2 x Opteron 2378 / 32GB DDR667-RE
EVGA GeForce 275 GTX / Tuniq 1000W PSU
Crucial 256GB M225 SSD (boot)
ARC-1120 PCI-X / 3 x 2TB Hitachi 7200 RAID5 (data)

I am having persistent issues getting Ubuntu to recognize (correctly)   the Crucial 256GB SSD. Although the SSD is recognized in the BIOS the   Ubuntu installer fails to register it as a viable partition on it's   first pass. If I reflash the BIOS of the SSD (using the "reflash" switch   on front) the drive is now recognized as a 256.1 GB partition (which I   think is erroneous, it should be more along the lines of 238 GB).

I've found a thread that seems to indicate that this might be due to a bug:

[http://ubuntuforums.org/showthread.php?p=8690795#post8690795](http://ubuntuforums.org/showthread.php?p=8690795#post8690795)

...but I'm having some trouble implementing an immediate solution from the details of the thread - at least, I don't really know how to pass the kernel boot parameters described in the thread, if indeed this is the workaround the author is suggesting. 

Any advice?

---

### Post by Bas232 on 2011-02-28
Go a few posts up and apply the kernel parameter.
I'm still running well on SSD without any problems.

> 
I added the kernel parameter libata.force=noncq after quiet splash.
nano /etc/default/grub 

After update-grub (all with sudo or root)

So new line reads:
> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libata.force=noncq"


And with the installer, add the option before you boot the installer.

---

### Post by aix1 on 2011-02-28
And if you try it, please let us know whether the kernel parameter helped. Thanks.

---

### Post by yemu on 2012-06-21
have the same issue with Vertex3 in ubuntu 12.04
i'll try to apply kernel parameter when I get home, but I also have two hdd drives apart from the ssd and I'm afraid it'll negatively affect hdd performance. is it possible to disable ncq only for ssd?

---

### Post by oldos2er on 2012-06-21
Please start a new thread for your question.

---

