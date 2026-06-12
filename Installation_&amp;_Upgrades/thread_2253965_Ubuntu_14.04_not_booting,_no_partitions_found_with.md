---
title: "Ubuntu 14.04 not booting, no partitions found with LiveCD"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by miina on 2014-11-23
Hey,

I managed to "lose" all the partitions while resizing one, using gparted. Would greatly appreciate any help.

My Ubuntu 14.04 was working on 64b system until I tried to resize a partition using LiveCD. Gparted stopped with error notice. After that gparted doesn't recognize any partitions at all.
I tried following this thread which seemed to have a similar issue: [http://ubuntuforums.org/showthread.php?t=2229307](http://ubuntuforums.org/showthread.php?t=2229307)

Booting normally shows the following notice:
```
2100: Detection error on HDD0 (main HD)
```
After continuing with Esc, I'm shown Boot Menu and Application Menu. Boot Menu showing two options: ATAPI CD0 and PCI LAN.

Then I used the LiveCD to figure out the issue.
Run the following command under sudo:
```
fdisk -l
```
This doesn't show anything.

I installed the Boot/Repair program which has the following output:
[http://paste.ubuntu.com/9206307/](http://paste.ubuntu.com/9206307/)

Then I installed the TestDisk program, ran it as sudo, and the only thing it shows me, is this:
```
Disk /dev/sr0 - 1010MB / 964MiB (RO) - MATSHITADVD-RAM UJ8C2
```

Any suggestions and help is greatly appreciated!

M.

---

### Post by oldfred on 2014-11-23
Nothing is showing hard drive.
If you go directly into UEFI/BIOS does it show the drive?
Was this an SSD? What brand?

---

### Post by miina on 2014-11-24
Thank you for the answer! Indeed I didn't check from BIOS.

BIOS->Config->Serial ATA (SATA) menu shows the following:

```
SATA Controller Mode Option [AHCI]
```
There is no other information.

And the BIOS->Startup->Boot shows ATA HDD0 in the list but without any information next to it. 
Does this mean that the BIOS can't recognize the HDD either? What could be the options?

For information: The laptop I'm using is Thinkpad 403s, with SSD.

Thanks!!

M.

---

### Post by oldfred on 2014-11-24
If BIOS does not see a drive, then no operating system or any disk tools will see it. BIOS has to report that a drive exists and some basic info on it.

I think to even run smart data tests drive has to be seen to be able to load the data from the drive.

I might double check connections, just to see if something happened to come loose.
Or maybe remove drive and mount in another system and see if it can be seen there.

---

### Post by miina on 2014-11-24
You were right, it seemed to be a connection issue!
Tons of thanks!!

After realizing that BIOS is not showing the hard drive, opened up the computer, re-connected HD and then it showed. 
Apparently during the partition change, connection with the HD was interrupted/lost, now the HD is recognized and although now there's data loss and grub-issues, this all is already for a known reason!

Thanks again!

M.

---

