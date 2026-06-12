---
title: "Linux Driver for ext DVD drive to install windows - Urgent (work computer)"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by seemore on 2011-06-14
I am running 10.04 LTS Lucid Lynx. 64 bit

I have to re-install windows 7 64-bit for work as this isn' my lap top (Dell m301z - no internal DVD drive). When windows prepares for setup it asks me for a driver for the ext DVD drive (SAmsung SE-S084C). The drive just worked from the first time I plugged it in and I never needed a driver. Now, I have searched far and wide for a driver and Samsung have nothing. Is there a generic ext DVD driver that might work? Otherwise I will be in some serious trouble.

Any help is appreciated.

---

### Post by seemore on 2011-06-15
Just a bump

---

### Post by uRock on 2011-06-15
Are you looking to write over the drive to install Windows or are you setting up a dual boot? 

Either way, you can boot an Ubuntu LiveCD/USB and use the partition editor found in the System> Administration menu to edit/remove the partitions and create the NTFS partition for Windows.

---

### Post by seemore on 2011-06-15
A new windows only. Work don't want to know about Linux.

---

### Post by uRock on 2011-06-15
> **seemore said:**
> A new windows only. Work don't want to know about Linux.

You can use an Ubuntu LiveCD to wipe out the EXT partition and create the NTFS partitions. If you need help with the partition editor, then let me know.

---

### Post by seemore on 2011-06-15
Thanks for your time. 

OK so make the NTFS partition and install windows 7 on to it, then delete the Linux partition?

---

### Post by uRock on 2011-06-15
> **seemore said:**
> Thanks for your time. 

OK so make the NTFS partition and install windows 7 on to it, then delete the Linux partition?

I'd use the Ubuntu LiveCD to delete all of the partitions, then create one NTFS partition using the whole HDD, then install Windows.

---

### Post by seemore on 2011-06-15
OK I'll try that.

---

### Post by wandalalakers on 2011-06-15
If you decide at a later date to put Ubuntu back on your work laptop, make a laptop image of your win 7.  Install Ubuntu again and make an image of that.  This way if you decide to put Ubuntu back on, you don't have to worry about the job finding out.  The end result will be:

1. Win7 64 bit laptop image
2. Ubuntu 64 bit laptop image

> **seemore said:**
> A new windows only. Work don't want to know about Linux.

---

### Post by seemore on 2011-06-16
There was no option of formatting the hdd to NTFS when booting from the ubuntu live cd. So I used gparted to change the file system to NTFS and then boot from the windows dvd. I still get the same driver error. When I try to boot from ubuntu cd I get "unrecognised file system grub rescue ". Now I am in a world of pain.

---

### Post by seemore on 2011-06-16
OK I can live boot. I won't touch anything further Until advised.

---

### Post by uRock on 2011-06-16
I used a VBox to make some screenshots to walk you through the repartitioning process. 
1. Boot the LiveCD and open the GParted application,
[ATTACH]195271[/ATTACH]
2. Deactivate Swap if it is still there and being used, otherwise skip this step,
[ATTACH]195272[/ATTACH]
3. Select Device> Create Partition Table, which will delete all of the partitions on the drive,
[ATTACH]195273[/ATTACH]
4. Click to create a new partition and select ntfs from the drop down menu, then click the green check mark to allow the partitioner to do its thing. Your Windows installer shouldn't have any problems utilizing the new ntfs partition.
[ATTACH]195274[/ATTACH][ATTACH]195275[/ATTACH]

---

### Post by seemore on 2011-06-17
Thanks for taking the time to post pictures. I have made some progress, but it still asks for the driver and doesn't accept the manufacturer's dvd, latest download from the manufacturer's website or dell driver dvd. I'm at a loss for what it wants. The file system is now ntfs. 

Next time I'll do the disc image idea or simply put ubuntu on an external hdd and boot from there.

---

### Post by seemore on 2011-06-17
Possible solution: boot win 7 from my external hdd (you could also use a hen stick with more than 5.5gb). 

Here are the instructions: [http://www.markwilson.co.uk/blog/2008/11/installing-windows-from-a-usb-drive.htm]("http://www.markwilson.co.uk/blog/2008/11/installing-windows-from-a-usb-drive.htm")

There is more than one way to skin a cat (or windows). How I've got a good feeling about this one.

---

