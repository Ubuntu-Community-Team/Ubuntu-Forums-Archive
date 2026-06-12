---
title: "No C: drive found during 18.04 install at disk partition step"
date: 2018-07-24
forum: Installation &amp; Upgrades
---

### Post by hiddenusername on 2018-07-24
While trying to install 18.04 on an old Dell Poweredge 2900 server, I get all the way to the disk partitioning section of the setup process and the HDDs are not recognized.  A message about installing the correct drivers comes up with a list of drivers to choose from to install.  I have recently removed one of the HDDs for another project so one of my questions is: will this affect the setup if two disks are still in the machine and does the order they are inserted into the machine matter?

A strange thing happens when a USB drive is installed at this point in the process.  The USB is recognized as the C: drive but I don't want it there.

Any thoughts?

---

### Post by ajgreeny on 2018-07-24
Linux does not use the C: drive nomenclature, so I do not fully understand what you are saying.

If you boot to a live system, open a terminal with Ctrl+Alt+T, and then run terminal command ```
sudo fdisk -l
``` from that you will see your disk(s) listed with current partitions in a style like this from mine.
```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F20E3B6B-401B-4F83-B31B-71780FC81217

Device          Start        End    Sectors   Size Type
/dev/sda1        2048     411647     409600   200M EFI System
/dev/sda2      411648   41371647   40960000  19.5G Microsoft basic data
/dev/sda3  1945128960 1953523711    8394752     4G Linux swap
/dev/sda4    41371648 1904168959 1862797312 888.3G Microsoft basic data
/dev/sda5  1904168960 1945128959   40960000  19.5G Linux filesystem

Partition table entries are not in disk order.


```
Note that the disk shows as /dev/sda and the partitions as /dev/sda1, /dev/sda2, etc etc, not C:, D:, etc etc as Windows uses, and where disks are often not real separate physical disks but are just partitions on a single disk; very confusing once you get used to Linux partition names and descriptions.

---

### Post by yancek on 2018-07-24
Might help if you indicated whether this install of Ubuntu is and will be the only operating system on the machine.  Can't imagine where a reference to a C drive would come from.

Having multiple disks should not affect anything IF you are familiar with Linux hard drive/partition naming conventions.  Otherwise, you could overwrite your data if you have any on any partitions/drives.i

---

### Post by hiddenusername on 2018-07-24
I see where I went wrong with the posted question now.

What I mean is that the HDDs are not seen by the installation software.  The USB is recognized as Local C: though if my memory serves me correctly.  I'm not implying that Ubuntu has anything to do with that but it is in the name of the USB so I assumed it had to do with the OS but I think for some reason the USB has that name even though I haven't given it that name.

---

### Post by yancek on 2018-07-25
Are you trying to install the Ubuntu desktop version with a full GUI or the server version with no GUI?
How many hard drives do you have?
Are they recognized in the BIOS?
Does this machine currently have any OS installed?

Local C seems like an odd name for a usb.  Generally when I have a usb I am using to boot from it will show in the BIOS by the manufacturer name, Sandisk, Lexar, Toshiba, etc.

---

### Post by slickymaster on 2018-07-25
*Thread moved to **Installation & Upgrades**.*

---

### Post by mastablasta on 2018-07-26
> **hiddenusername said:**
> While trying to install 18.04 on an old Dell Poweredge 2900 server, I get all the way to the disk partitioning section of the setup process and the HDDs are not recognized.  A message about installing the correct drivers comes up with a list of drivers to choose from to install.  I have recently removed one of the HDDs for another project so one of my questions is: will this affect the setup if two disks are still in the machine and does the order they are inserted into the machine matter?


no it shouldn't matter.

what drivers? hard disks have to be formatted first. if they are preformated then they should show as emtpy disk sapce.

> 
 A strange thing happens when a USB drive is installed at this point in the process.  The USB is recognized as the C: drive but I don't want it there.


change the volume name of the USB (on windows you can do it in properties or use label command for this.: [https://en.wikipedia.org/wiki/Label_(command)](https://en.wikipedia.org/wiki/Label_(command))

that way it won't confuse you.


otherwise any chance of getting a screenshot of what exactly you see at partitioning screen?

---

