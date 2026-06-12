---
title: "EXT4 disk dissapeared"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by vinylgroover on 2009-11-22
I've just upgraded to 9.10, the installation was ok but my startup time is now considerably slower than 9.04.  Anyway that's not my main problem... I've got 2 SATA hard drives, one has ubuntu running on it and the other one is a backup & media drive. The main ubuntu drive is running EXT3 and the media is/was running EXT4.

[FONT=monospace]Everything was fine in 9.04 but now when I load up my computer, the other SATA disk doesn't appear.[/FONT] It shows up in the BIOS but not in ubuntu. I took the drive out and put it in an external hard drive case then plugged it in via usb... here is my dmesg

```

[  133.389520] usb 2-4: new high speed USB device using ehci_hcd and address 6
[  133.523475] usb 2-4: configuration #1 chosen from 1 choice
[  133.525015] scsi7 : SCSI emulation for USB Mass Storage devices
[  133.525119] usb-storage: device found at 6
[  133.525127] usb-storage: waiting for device to settle before scanning
[  138.524207] usb-storage: device scan complete
[  138.528444] scsi 7:0:0:0: Direct-Access     Maxtor 6 L200M0                PQ: 0 ANSI: 2
[  138.528864] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  138.550559] sd 7:0:0:0: [sdb] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[  138.552799] sd 7:0:0:0: [sdb] Write Protect is off
[  138.552802] sd 7:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  138.552804] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  138.576672] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  138.576676]  sdb: sdb1
[  138.629058] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  138.629063] sd 7:0:0:0: [sdb] Attached SCSI disk
[  139.611671] device-mapper: table: 252:0: mirror: Device lookup failure
[  139.611676] device-mapper: ioctl: error adding target to table
[  140.849039] device-mapper: table: 252:0: mirror: Device lookup failure
[  140.849043] device-mapper: ioctl: error adding target to table
[  141.739766] device-mapper: table: 252:0: mirror: Device lookup failure
[  141.739771] device-mapper: ioctl: error adding target to table
[  142.438378] device-mapper: table: 252:0: mirror: Device lookup failure
[  142.438382] device-mapper: ioctl: error adding target to table
[  143.320507] device-mapper: table: 252:0: mirror: Device lookup failure
[  143.320511] device-mapper: ioctl: error adding target to table
[  144.072061] device-mapper: table: 252:0: mirror: Device lookup failure
[  144.072065] device-mapper: ioctl: error adding target to table
[  145.085044] device-mapper: table: 252:0: mirror: Device lookup failure
[  145.085049] device-mapper: ioctl: error adding target to table
[  145.747090] device-mapper: table: 252:0: mirror: Device lookup failure
[  145.747095] device-mapper: ioctl: error adding target to table
[  146.615889] device-mapper: table: 252:0: mirror: Device lookup failure
[  146.615894] device-mapper: ioctl: error adding target to table

```Any clues what's wrong? I really cant afford to loose the stuff on the hard drive! It shows up in Gparted now but its just blank with a warning triangle. Do I need to install EXT4 support or something so that it can be read by ubuntu?

---

### Post by fancypiper on 2009-11-22
Did you run fsck on that parition?

---

### Post by vinylgroover on 2009-11-22
I'm running fsck now but its taking forever.  Would I be crazy in thinking that somehow karmic decided to make a RAID array using this hard drive?

---

### Post by wilee-nilee on 2009-11-22
You might benefit with a fresh install of Karmic if you have the important data on another HD.

---

### Post by presence1960 on 2009-11-22
> **wilee-nilee said:**
> You might benefit with a fresh install of Karmic if you have the important data on another HD.

you can't mount an ext4 filesystem from an ext3 filesystem! if you want to mount that data disk your Ubuntu OS must also be ext4. That is why I keep my data disk ext3- it can be mounted from either ext3 or ext4 filesystems.

---

### Post by vinylgroover on 2009-11-22
It worked fine with 9.04, and that was running ext3.  I don't even know why I formatted this an ext4 drive in the first place, its probably going to be a costly mistake!

---

### Post by presence1960 on 2009-11-22
> **vinylgroover said:**
> It worked fine with 9.04, and that was running ext3.  I don't even know why I formatted this an ext4 drive in the first place, its probably going to be a costly mistake!

I used to have Hardy 8.04 as a backup OS and it was ext3. I could never mount jaunty 9.04 which was ext4 from it. I know for a fact an ext3 OS can not mount ext4.

You can save your data. boot from the Ubuntu Live CD or backtrack linux CD and copy your files from the data partition over to another location. Then format the data partition to ext3 and then copy files back.

or reinstall Ubuntu as ext4.

---

### Post by wilee-nilee on 2009-11-22
> **presence1960 said:**
> you can't mount an ext4 filesystem from an ext3 filesystem! if you want to mount that data disk your Ubuntu OS must also be ext4. That is why I keep my data disk ext3- it can be mounted from either ext3 or ext4 filesystems.

And your point is by using my comment? my solution would have two ext 4's. I don't know if ext4 can open another but it would seem that it could, although I wouldn't make any changes without checking 1st.

Okay  get your point a media on ext 3 makes more sense I agree. Personally I have mine with ntfs that way it isn't a door stop since it is a external when I visit a other OS system not Linux.

---

### Post by presence1960 on 2009-11-22
> **wilee-nilee said:**
> And your point is by using my comment? my solution would have two ext 4's. I don't know if ext4 can open another but it would seem that it could, although I wouldn't make any changes without checking 1st.

Okay  get your point a media on ext 3 makes more sense I agree. Personally I have mine with ntfs that way it isn't a door stop since it is a external when I visit a other OS system not Linux.

My post was not directed towards you. I just gave the OP two options. One was to reinstall Ubuntu as ext4 and the other was to back up the ext4 data disk, format it to ext3 and then restore the backup.

Either way the OP would be able to access his/her data.

---

### Post by wilee-nilee on 2009-11-22
> **presence1960 said:**
> My post was not directed towards you. I just gave the OP two options. One was to reinstall Ubuntu as ext4 and the other was to back up the ext4 data disk, format it to ext3 and then restore the backup.

Either way the OP would be able to access his/her data.

Your explanation of a ext3 for media makes total sense, but this was done with using my comment, I think this is okay but a better explanation of it would have been helpful. You didn't have to use my quote at all your point was self evident and stood alone as a valid idea. 

Since I have a dual boot of W7 and Karmic I never follow the separate partition for home that can be mounted after upgrading or read from a MS system. I think this works for some but a external HD is a better way of backing up your stuff for me.

---

### Post by presence1960 on 2009-11-22
> **wilee-nilee said:**
> Your explanation of a ext3 for media makes total sense, but this was done with using my comment, I think this is okay but a better explanation of it would have been helpful. You didn't have to use my quote at all your point was self evident and stood alone as a valid idea. 

Since I have a dual boot of W7 and Karmic I never follow the separate partition for home that can be mounted after upgrading or read from a MS system. I think this works for some but a external HD is a better way of backing up your stuff for me.

I didn't read your comment prior to posting. Not trying to steal your thunder.

---

