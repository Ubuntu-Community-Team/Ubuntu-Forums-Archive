---
title: "Cannot Install Ubuntu from CD/Flash Drive onto HD with Windows7"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Viper442 on 2010-06-10
My computer:
I have a primary hard drive with 500gb.  I am using windows 7 64-bit and installed it without partitioning.  I want to install ubuntu 10.04 and so I shrunk the drive (using windows manage) by 100gb for the installation.  

I also have 2 storage drives, 1.5TB and 1.0TB.

My procedure:
I downloaded the 64bit ubuntu .ISO and used netbootin to put it on my 4gb flash drive.  I get the error, "No DEFAULT or UI configuration directive found" when selecting "USB-HDD" as my boot device(F12).

After repeatedly formatting and retrying this procedure, I decided to burn a dvd with the ISO.  When I do this and boot from CD/DVD it begins to load UBUNTU.  It brings up the loading page with the 5 dots that continually fill and empty and then goes to a black screen saying some error.  I forgot to write it down...

Strangely, if I leave the USB drive in and try to boot from CD, it will load into installation and I can 'TRY" or "INSTALL."  I even tried letting it get into this stage, then pulling the USB drive(maybe not recommended), and it won't let me proceed.  It is almost as if it needs the CD to boot, but then uses the flash drive to install.

Anyway, I choose "largest free space" and it selects 104GB on sda.  At this point, it is still "unallocated space."  I hit forward and it gives a review of my options, or I can select "advanced" to change the boot manager.  I left it alone, boot manager is "sda" for partition #5,#6.  It gets to 15% and gives this error:
"end of file while reading no such file or directory."  I am forced to click continue or cancel and it reads:
"The creation of swap space in partition #6 of SCSI1 (0,0,0) (sda) failed."

So I am now stuck and seek advice.  I can "TRY" and in fact am typing this in that mode now.  I opened GParted and it shows my 2 storage drives and the flash drive, but does not show the 500gb primary HD that I use to boot windows.  This seems strange to me.  

Here is a further possible blunder I have done.  I figure I'll try to install it onto one of my storage drives to see if it will work.  So in GParted I select "Move" and drag the bar 50gb to the left.  I assume this is the same as "shrink" from windows 7.  It begins and is taking 3.5 hours to complete.  I thought about cancelling, but it says it may cause SEVERE file damage, so I am currently sitting here letting it carry out.

So I have 2 main questions:
1) Is my immediate action (moving the 1.36TiB to 1.32TiB to the left and shrink it) doing any real damage?  Is it reversible and is it essentially the same as Shrink from Windows 7?  I know I can "Expand" in Windows 7 to undo it, but that operation seemed to take seconds, where as this operation is taking hours.

2)  What suggestions are there for me properly installing a dual boot of Windows 7 and Ubuntu with Windows 7 already installed.  I have read over many guides and tutorials, and I thought I was doing it correctly, but it is not installing properly.

I hope that this is enough information to give an idea of what my problem is.  It is my first attempt at ubuntu and so I am fairly lost.  I don't want to attempt anything else that might corrupt my system.  I already regret using GParted in the way that I have.

Thanks in advance,
-Eric

---

### Post by efflandt on 2010-06-10
Shrinking and moving a partition are vastly different.  Shrinking a partition is simply a matter of moving any files necessary lower on the partition and updating the partition table and FAT (file allocation table).  That happens relatively quickly, maybe a few minutes if not a few seconds.

I think moving a partition involves moving everything on the partition, so all files are the same offset from the beginning of the relocated partition, because some files in a different location may break.  For example when you defrag Windows, you will notice that it shows some files that cannot be moved (virtual memory, etc.), so they need to be the same relative location on the moved partition.  So to be on the safe side, everything on the partition is moved.  That can take many hours depending upon the partition size.  Moving is reversible, but would also take a long time, so you might want to temporarily disable power saving settings other than your monitor.

I may be old school, but frankly I like to manually set up my partitions, instead of relying on automatic partitioning, because sometimes automatic partitioning may not end up like you want it, or may even break things.  Years ago, 64-bit WinXP Pro beta changed my partition table geometry (cylinders and heads), so it could not even boot itself, much less XP Home.  Since I had not recorded Linux fdisk, but only glanced at it after partition resizing, it took some trial and error from memory to restore partition table geometry.  Then when I was installing SuSE (8.2 I think), I recognized from figures it quoted that it was about to do the same thing.  So I told it no, use this partition for swap and that partition for / as is.

I have one PC that boots fine from far end of its 200 GB internal drive or 160 GB USB drive, but cannot boot from a 500 GB USB drive (that drive boots fine on 2 other computers).  So sometimes it is possible to run into BIOS issues with older PCs and newer larger drives.

---

### Post by Viper442 on 2010-06-10
Well, at least I am only wasting 5 hours of my life with that move command instead of irreversibly destroying my 700GB of media I'd rather not lose.  I wish I could cancel it.  I'll have to reverse it later.  I appreciate the help.  

I do still require some assistance with my installation though. Since I have been sitting here waiting 3 hours, I have been familiarizing myself with ubuntu a bit.  I have noticed that the 500gb HD shows up in Disk Utility now.  Previously it would say "unknown volume."  Now it correctly shows 395GB Unknown and 105GB Free.  I wonder if it will have the same problem when I try to reinstall it.

So using manual options:
I cannot check the options now, but when I choose to manually partition the 105 GB, what option should I choose?  There were several options.  I do not know if any of these will alleviate my problem with the errors I mentioned above, but it is worth a shot later tonight.  I will google it up as well to see if I can figure something out.

-Eric

---

### Post by oldfred on 2010-06-10
One more advantage of manual partitioning is you can add a partition for /home and/or an extra NTFS partition for shared files with windows. I liked having the same firefox and thunderbird in both when I was converting from XP. Another advantage of manual partitioning is after setting partitions you can check that windows works before installing. 

With data on separate partitions you only need 10 to20GB for root (/), 2GB or total RAM (if hibernating) for swap and the rest for /home.

My system with many programs added is 6GB. You may need temp space for up to the 4GB that it takes to write a DVD. Since I have all data in data or shared partitions my /home is only 1GB. 

Even experienced windows users suggest a separate NTFS partition for windows data so when you have to reinstall windows you do not lose your data. I prefer to only read from system partitions with other operating systems and read/write in shared or data partitions.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

An advantage to having Ubuntu on the second drive is that you can install its boot loader to the second drive and not delete the windows boot loader. Just change in BIOS to boot the second drive. But you have to use the advanced button to make sure your install grub to the second drive.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Some with large data drives want an operating system on every drive.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

