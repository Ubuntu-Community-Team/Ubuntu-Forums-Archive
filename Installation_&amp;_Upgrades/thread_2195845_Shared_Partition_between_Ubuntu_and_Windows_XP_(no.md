---
title: "Shared Partition between Ubuntu and Windows XP (not working)"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by erikscomp56 on 2013-12-26
Hey guys, so recently I purchased a new hard drive to serve as a back up. It is 3TB (way more than I need) so I decided to use about 500 gigs to serve as back up for my Windows XP files (Windows is my primary OS) and the rest of the hard drive I'm going to devote to Ubuntu. 

As you all know, with hard drive greater than 2TB, the hard drive is formatted in GPT, which windows does not recognize (the infamous 746 GB of unusable space). I took care of that problem separately and succefully partitioned 500 GB of the hard drive to serve as a back-up space, I named the partition "Refrigerator" (ever heard of deep freeze? pun intended) So anyway, I tested the new drive out and put some of my music in there to make sure it works, and surely enough, it does. Windows obviously doesnt see the remainer of the hard drive, but I dont care for that, it sees the 500 GB NTFS partition I created for it, and that's all I need it to do. 

[Enter Linux] 

So today I decided to install Ubuntu (13.04), during the set up from a live USB, I selected the 3TB hard drive, and I could see the 500 GB NTFS partition, and the remaining 2500 GB of free space. I created a /BOOT, swap space, and / partition (root being 2TB total). The installation went smoothly and the system rebooted, straight into Ubuntu. In ubuntu I could see my root directory with 1.9 TB of free space (exactly as it was supposed to be) I can see my 246 GB hard drive (a separate hard drive, where Windows resides) and most importantly I could see a 500 GB partition named "Refrigerator"

This was the very partition I created in Windows for back up. I mounted and opened it, and inside was my music that i had stored earlier through windows. Everything was as it should be, but then I booted into Windows (gotta love GRUBs ability to detect all bootable devices instead of just Linux :D) 
but Windows can no longer see the 500 GB back-up partition. It CAN see an extra drive (:F) just as before, but if I double-click it, it tells me the drive must be formatted (which cant be true, my files are STILL in there, I can see this through linux). And if I enter the disk manager, Windows is back to the annoying 746GB of unusable free space. 


I was hoping that if I formatted the drive the way Windows wants, and set up a back-up system, the way windows wants, I could later install ubuntu (who isn't nearly as picky and annoying) on the remaining free space without disturbing the pre-formatted "Refrigerator" so as not to offend windows. It appeared to work initially, as linux has no problem in mounting and browsing the partition (even still calls it by its name that I set up in Windows), but for some reason Windows is acting stupid and can't see it.

Does anyone know a way to get around this? 
Did I do something wrong during the installation of Linux?

I realize that I can just move files over from the Windows hard drive to the "Refrigerator" via Linux, but as I stated earlier, Windows is my primary operating system, I need to be able to quickly back-up important data without having to boot into a completely different OS.

---

### Post by oldfred on 2013-12-26
It is my understanding that XP does not work with gpt partitioned drives. It does not have drivers for that.

So how did you create your 500GB partition. Was that really MBR(mdos) and then you converted 3TB drive to 2TiB drive?
But Ubuntu then may have converted drive to gpt? It normally will install to large drives with gpt partitioning.
       
MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Post this:
sudo parted -l

---

### Post by erikscomp56 on 2013-12-27
Hi oldfred

Thanks for the response

Well, here is the thing, I used the disk management program in Windows to format and partition the hard drive (when it was new), back then it had the GPT flag on the drive. After I did the formatting, windows was OK with the drive, which (i think) means the drive MUST have been reformatted into MBR. Also when I looked at the drive in disk management after the formatting, it no longer had the GPT flag. 

So at this point, I am convinced the hard drive had been converted to MBR, and only a limited amount was available for use (which I was ok with) 

Then when I was installing linux, I had trouble with partitioning the hard drive at first ( I accidentally left it on "Logical" instead of "Primary") so I got error codes about ms-dos not being able to handle the operation (not sure what the error was exactly, I didn't think of it much after I fixed the partition type). The important thing is that even linux recognized the hard drive to be formatted in MBR, not GPT.

After the installation was complete, and I found out that Windows no longer sees the "Refrigerator", I re-opened the disk manager, and I could see the classic 746 GB of unusable space, BUT this second time around, it did NOT have the GPT flag on it. This is why I discounted the idea that the drive was replaced back into GPT format, and I thought maybe the Ubuntu installer would have notified me if the disk needed to be reformatted. 

Maybe I have it all wrong, not too sure, but its no big deal, I have nothing on it that I am afraid to lose, so I can reformat it a million times before I get it right :)
I will do my due diligence and find what went wrong, I was just looking for possible obvious marks that I missed on the way.

Edit: Also I forgot to reiterate, after the successful linux installation, I was still able to access all my music files that I had placed into the "Refrigerator" partition. If linux had reformatted the drive from MBR to GPT, wouldn't at least some of those files been corrupted in the process? 

Thanks

-Eric

---

### Post by oldfred on 2013-12-27
If you can read data that is good.

You can convert drives to/from gpt and MBR. And there is hybrid gpt/MBR sometimes used by Macs which use gpt to boot Windows in BIOS/MBR mode.

Post this, change from sda to your drive.
       sudo parted /dev/sda unit s print
and this, you may have to install gdisk
sudo apt-get install gdisk
      
 sudo gdisk -l /dev/sda

Not normally recommended:
      
 [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

 Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[URL="http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html"]http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html

[/URL]

[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

### Post by erikscomp56 on 2013-12-27
Hey, I did not get a chance to do what you asked me to do, but I did get it working! 

It looks like the problem was exactly as you suspected, the hard drive was reformatted into GPT during Linux installation. Here is what happened:

In my frustration with my original plan not working, I reformatted the hard drive again through Windows, same size 500 GB and everything. I wanted to see if this would corrupt the Linux installation because I was interested if formatting works on the entire drive, or only the beginning 746 GB that windows sees.

After I reformatted it and set up 500 GB "Freezer" drive, I opened it, to make sure it works, and placed a PDF file inside. 

After this I rebooted, my boot sequence was set up to boot from the 3TB hard drive first (which has GRUB) which then identifies the 246 GB windows hard drive and lets me boot it. However the computer crashed immediately after trying to boot from the 3TB hard drive. So the Linux (or at least GRUB) files had been corrupted by the reformatting that I did through Windows.

I proceeded to reinstall Ubuntu from the live usb I originally used, only this time, I gave the /boot partition 500MB of space, 5GB for swap and 1TB for root. I did this intentionally to keep the total space well below the MBR 2TB restriction. I thought maybe because I partitioned more than 2TB in my initial installation, the hard drive was forcefully reformatted into GPT. 

The installation went normal, and just as before, in Ubuntu I could see the "Freezer" drive, mounted 500 GB with the very same pdf file i placed in it earlier through Windows. Nothing new. Then I booted into windows, and this time around the Freezer drive was still there, fully accessible with my pdf file still in there. Also when I open disk manager, Windows now sees the 500 GB Freezer partition, the 500 MB boot partition, 5GB swap and 980-something GB root partition. Ofcorse it can't access any of the Linux partitions (no surprises) but it does recognize them. 

In total, right now I have access to about 1.505 TB of room, 500 GB shared, 1000 GB for Ubuntu.

I think more than likely, the hard drive got reformatted into GPT during my initial installation, because that one totaled to 2.5TB. 
The ms-dos error I was getting earlier (that had me believe the hard drive was in MBR) was popping up before I committed the new partition table. I assume after submitting it, linux was forced to reformat to GPT because of the partition sizes (I still dont know why I was able to access my data after the formatting though, maybe switching from MBR to GPT doesnt corrupt data?). 

Thanks for your help!
Hopefully someone else finds this info helpful

(Happy upcoming new year)

---

### Post by oldfred on 2013-12-27
Glad you got it working. :)

Later when XP expires, you then may want to convert drive to gpt to get full use.

---

### Post by erikscomp56 on 2013-12-27
I was hoping of switching to Linux permanently once I got a new hard drive, but alas until AutoCAD or SolidWorks begin making their software Linux compatible, I will have to dual boot :/
Oh well, XP is nearly obsolete anyway, I'm sure I'll have better luck with a newer 64 bit Windows haha

---

