---
title: "Fresh intsall of Lubuntu 17.10 works on usb boot but will not install"
date: 2017-12-08
forum: Installation &amp; Upgrades
---

### Post by cal.mac on 2017-12-08
Hi,

I've tried a fresh install of Lunbuntu 17.10 on a samsung N130 that preiously had lubuntu 13.something on it and would not update or install anything. I hadn't used it for a few years but decided to take it traveling to peru because its small and worthless (having forgotten how bad it was)  it's turned out to be almost unusable so I bought a flash drive and downloaded 17.10 at an internet cafe, it now boots from the usb, but when I try to install to the hard drive (erase and install) it gets stuck at LVM(?) auto partion section tell me its failed and to check /var/log/syslog for more information. When I enter this into LXTerminal (is this correct?) it returns 'permission denied'.  Having said that when I boot without a USB it shows the desktop of 17.10 in the right hand fith of the screen, the rest is black and their is no response to any inputs.

I suspect a partitioning problem, Could one partition be write protected? I've had a look through the bios to see if the HDD is write protected it doesn't seem to be. I don't think there are any secutriy setting in the bios stopping the install working but I don't know much so could easily be wrong.

I don't know much about computers or linux so please excuse any stupid mistakes or omissions and be as patronising and simple as possible with any questions or answers.

Thanks for your time 
Calum

P.s. I think the problems with the previous Lubuntu 13.something started after an update of that OS.

---

### Post by yancek on 2017-12-08
If you can boot the new Lubuntu on the flash drive, do that and open a terminal and post the output of:  sudo gparted   I'm not sure if Lubuntu has gparted on the iso, if that doesn't work do:  sudo parted -l (Lower Case Letter L in the command) and post the output here.  That should show the drive/partition information.  You should not have LVM with an Erase disk and install, at least I would not expect that.  You may have to create a new partition table on the drive.

I'm not really clear on your circumstances.  Downloading Lubuntu just gives you the iso, did you then put the Lubuntu iso on a flash drive?  If so, what software or method did you use to do this?  

> /var/log/syslog 

That's a log file and you need to use a text editor and have root permissions to access it:  sudo leafpad /var/log/syslog 

The problems with the screen are something else.

---

### Post by vasa1 on 2017-12-08
> **yancek said:**
> ... sudo leafpad /var/log/syslog 
...
The file is readable even without elevated privileges for me.

---

### Post by cal.mac on 2017-12-15
Hi sorry for the slow reply, I was away from the internet.

The output of gparted is;
Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/rofs.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-999.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
======================
libparted : 3.2
======================


sudo parted -l gives;

======================Model: ATA SAMSUNG HM160HI (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  79.9GB  79.9GB  primary  ext4         lvm


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8004MB  8003MB  primary  fat32        boot, lba


Model: Unknown (unknown)
Disk /dev/zram1: 525MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  525MB  525MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram0: 525MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  525MB  525MB  linux-swap(v1)


So it apears the drive has two even partions, not sure why? I don't think I did this.

I downloaded Lubuntu and used universal usb installer on a windows 8 machine to make the bootable usb.

---

