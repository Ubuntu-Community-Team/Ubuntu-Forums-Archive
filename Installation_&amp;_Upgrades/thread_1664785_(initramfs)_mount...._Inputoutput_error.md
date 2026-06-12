---
title: "(initramfs) mount.... Input/output error"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by shinigami82654 on 2011-01-11
So I *had* Ubuntu Netbook 10.10 installed and loved it compared to Windows XP. It installed with slight difficulty but I got it working. Anyways I ended up getting something on my computer that had a corrupted file on startup. This caused my netbook to start just fine, I would login and within minutes it would start lagging, have the menu bar and side bar disappear, and then eventually back to login. At least thats what happened the most often. I tried reinstalling and getting rid of my current OS (with the same thing) but after installation it wouldn't work. (I can't remember what was happening there.)

I gave it to my friend's dad who's job is to fix computers (he even worked for microsoft for a time) and apparently something that was on the computer forced my poor little SDD (8GB ._.) to overlap on itself and he wiped the disc for me.

Now when I try to boot from a live usb I get this error: 
```
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) mount: mounting /dev/sda1 on /casper-rw-backing failed: Input/output error
```
I've tried a 2GB PNY flashdrive and then tried my 1GB Lexar that I used to install UNR the first time. Neither work but I am typing this now off of the very same netbook by running Slitaz liveusb off of the PNY. Can someone please explain what the code means and how to fix it?

Thanks,
shinigami

---

### Post by shinigami82654 on 2011-01-11
Help would very much be appreciated. I'm still quite stuck.

---

### Post by shinigami82654 on 2011-01-13
Has anyone even seen this?

---

### Post by Rubi1200 on 2011-01-13
I haven't used SliTaz, but I assume it has a terminal.

Run these commands please and post the output here:

```
sudo parted -l

sudo fdisk -lu

sudo sfdisk -V
```

Best to just copy/paste the commands so there are no syntax errors.

Thanks.

---

### Post by psusi on 2011-01-13
> **shinigami82654 said:**
> Can someone please explain what the code means and how to fix it?


It means the flash is failing, or was corrupted.  If it shows up as /dev/sda, then run sudo badblocks /dev/sda to test it.

---

### Post by shinigami82654 on 2011-01-19
sudo parted -l
 
```

Model: ATA SSDPAMM0008G1 (scsi)
Disk /dev/sda: 8070MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number    Start       End         Size          Type            File system    Flags
1             1049kB    7671MB   7670MB     primary       ext3
2             7672MB   396MB     396MB       extended
5             7672MB   396MB     396MB       logical         linux-swap
 
Model: USB Flash Memory (scsi)
Disk /dev/sdb: 2004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number    Start       End         Size          Type            File system    Flags
1             32.3kB    2003MB   2003MB     primary        fat32             boot, lba
 
Model: Lexar JD Lightning II (scsi)
Disk /dev/sdc: 1002MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number    Start       End         Size          Type            File system    Flags
1             31.7kB    1002MB   1002MB     primary        fat32             boot

```
 
sudo fdisk -lu
 
```
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
 
    Device Boot     Start               End        Blocks    Id  System
/dev/sda1            2048      14983167     7490560    83 Linux
Partition 1 does not end on cylinder boundary
/dev/sda2     14985214      15759359       387073     5  Extended
Partition 2 does not end on cylinder boundary
/dev/sda3     14985216      15759359       387032    82 Linux swap
 
Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
 
    Device Boot     Start               End        Blocks    Id  System
/dev/sdb1    *          63        3913055     1956496+  c   Win95 FAT32 (LBA)
 
Disk /dev/sdc: 1002 MB, 1002438656 bytes
31 heads, 62 sectors/track, 1018 cylinders, total 1957888 sectors
Units = sectors of 1 * 512 = 512 bytes
 
    Device Boot     Start               End        Blocks    Id  System
/dev/sdc1    *          62        1956595       978267     b  Win95 FAT32

```
 
sudo sfdisk -V doesn't seem to work with Slitaz
 
I also ran badblocks, it thought for awhile. Is anything supposed to pop up?

---

### Post by Rubi1200 on 2011-01-19
Try using the Disk Utility tool from System > Administration.

I don't know of it will recognize the drive, but if it does look at the SMART information.

The relevant sections are:
Reallocated Sector Count
Current Pending Sector Count
Uncorrectable Sector Count

See what the values are and post here.

Thanks.

---

