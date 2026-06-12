---
title: "Win 7 &amp; Ubuntu dual boot - partition &amp; file access ?"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by Longstreet on 2011-03-24
Hello all. Sorry if this has been asked before. I've done quite a bit of searching, and the answers I've found have only confused me further. Any advice would be appreciated.

I want to dual boot Win 7 & Ubuntu, on an Aspire One D255, N455, 160 GB HD, 1G RAM. What I'd like to do is partition the hard drive so that most files (docs, music, videos, etc) would be available from either OS. I'm not sure if this is something I need to do when partitioning, or if they would be available regardless.

The pages I've seen on partitioning have left me scratching my head. I'm not sure what I'm shrinking, not sure how much space I need to leave for Win or Ubuntu, how to format the drive so files will be available to both...in short, I'm at the point where I know just enough to screw things up royally!

Can one of you walk me through this? Or is there a good tutorial on partitioning/allocating/formatting that will hold my hand as I do? I'm anxious to get Ubuntu working on this machine, with an eye towards using Ubuntu almost exclusively. Just not sure if I know what I'm doing.

Thanks in advance. I'd like to get Linux installed so I can start working on why my wireless card won't work (at least when running the Live CD! :)  )

---

### Post by Zzl1xndd on 2011-03-24
It will depend on how big the hard drive is. But I like to give each OS about 50-70 gigs (Mind you I am working with terabyte hard drives).

Ubuntu should be able to read anything on your Windows Partition but Windows will not be able to read your Ubuntu partition. As this is the case you will likely want 3 partitions. 1 for each OS, and one for your files. The one for your files should be the largest one and I would format it NTFS as both Windows and Ubuntu should be able to access it.

Hope this helps.

---

### Post by Longstreet on 2011-03-26
> **tweakedenigma said:**
> It will depend on how big the hard drive is. But I like to give each OS about 50-70 gigs (Mind you I am working with terabyte hard drives).

Ubuntu should be able to read anything on your Windows Partition but Windows will not be able to read your Ubuntu partition. As this is the case you will likely want 3 partitions. 1 for each OS, and one for your files. The one for your files should be the largest one and I would format it NTFS as both Windows and Ubuntu should be able to access it.

Hope this helps.

That does help. I've only got 160 G hard drive to work with, but considering my last laptop was a Vista Ultimate machine, with only 80G and TONS of music, pics and docs, and I still had only used ~55G, I don't think I'm going to run into space problems. I plan on 30 for each OS, and the rest for storage (7 Starter is pretty light for a Win OS).

In prepping for this, when I (from Windows Disk Management utility) shrink space on the HD, what exactly am I shrinking?

As a side note, wifi is working now, from the Live CD, so I expect the install won't be a problem there. Turns out I needed the Broadcom STA driver. Turning my attention now to the SD card reader...

---

### Post by Unterseeboot_234 on 2011-03-26
Let me give you my experiences. I have AMD64 with a sata-A came pre-loaded with Win7. I added sata-B for Ubuntu. Both hard drives have 1000-gig. The Ubuntu I partitioned back to 300-gig to keep things faster for files. What I learned is you MUST a partition the Win side with a NTFS format. Win7 HAS to do the format otherwise Win7 won't see the partition.

Do NOT let Windows format eFAT. Win7 does not offer FAT32. eFAT is patented proprietary POS. Nobody but Microsoft uses eFAT that I am aware of. That includes Flash cards, speed sticks and external hard drives.

Be SURE you look up the USB device in the Win7 control panel and Safely Unmount the device. Otherwise, Win7 has to reformat the device. Strange, that you can connect a blank formatted FAT32 device, but if after some use you fail to Safely Unmount, Win7 will remember that fact and block any other re-connection.

Do not Restart from Windows. Do a complete shutdown. Win7 has it's own idea of time and does not seek the BIOS clock. If you restart from Win7 and go into Ubuntu the clock will be off by a time zone.

Then, we get into Win7 concept of "Libraries" based upon User Accounts. I'll let you tangle with all that. Any more, I just email files back and forth.

If Win7 didn't have the nifty FAX program and if my wife's business didn't require Internet Explorer to get business information, I would reformat the Win7 drive. I hate how Win7 does a silent backup on Sunday night and waste 5-10 megabyte of locked, zipped, and hidden files.

I've probably hurt some feelings on the Windows7 forums and the Microsoft Windows 7 support sites. Somewhere in India I got the response back to change my CMOS battery to keep the correct time between boots if Ubuntu was giving me problems. (On a new computer???)

---

### Post by hello2012 on 2011-03-27
> **Longstreet said:**
> Hello all. Sorry if this has been asked before. I've done quite a bit of searching, and the answers I've found have only confused me further. Any advice would be appreciated.
 
I want to dual boot Win 7 & Ubuntu, on an Aspire One D255, N455, 160 GB HD, 1G RAM. What I'd like to do is partition the hard drive so that most files (docs, music, videos, etc) would be available from either OS. I'm not sure if this is something I need to do when partitioning, or if they would be available regardless.
 
The pages I've seen on partitioning have left me scratching my head. I'm not sure what I'm shrinking, not sure how much space I need to leave for Win or Ubuntu, how to format the drive so files will be available to both...in short, I'm at the point where I know just enough to screw things up royally!
 
Can one of you walk me through this? Or is there a good tutorial on partitioning/allocating/formatting that will hold my hand as I do? I'm anxious to get Ubuntu working on this machine, with an eye towards using Ubuntu almost exclusively. Just not sure if I know what I'm doing.
 
Thanks in advance. I'd like to get Linux installed so I can start working on why my wireless card won't work (at least when running the Live CD! :) )
 
[FONT=Times New Roman][SIZE=3]Actually, that’s nothing serous if you ask the same or similar problem here. [/SIZE]
[SIZE=3]From your question, even I do not very specialized in Ubuntu, I know there are many people choose it and for dual boot with Windows OSs. Considering you only have 160GB hard drive, if your previous OS is Windows 7 and you want to install Ubuntu based on exist Windows 7, you can divide 25GB for Windows 7 and create another partition go with 25GB as well for Ubuntu. Then, the remaining 110GB you also can distribute then again for your own needs. Windows 7 can help you create partition but there are many limitation, I believe you know the particularly limitations, so, you can also turn to some partitioning utilities for help. Here is partition software store I know, it displays some famous partition tool, you can get a look at:[/SIZE]
[[SIZE=3]http://www.partition-magic.com[/SIZE]]("http://www.partition-magic.com/")[SIZE=3] [/SIZE]
[SIZE=3]Furthermore, the partitions or files can be visited when you running any os.[/SIZE]
[COLOR=black][[SIZE=3][COLOR=#800080]http://www.partition-magic.org/res/repartition-hard-drive.html[/COLOR][/SIZE]]("http://www.partition-magic.org/res/repartition-hard-drive.html")[SIZE=3] [/SIZE][/COLOR]
[/FONT]

---

### Post by Sean Moran on 2011-03-28
[IMG]http://www.portstar.org/img/aophdd/aophdd017.png[/IMG]

Windows 7 seems to like a little more than 8192 Mb so that's why it gets 16384Mb as /dev/sda1.  

Standard Ubuntu root is 8Gb on /dev/sda2, and there's room for testing new distros on /dev/sda5 & 6, again each only needs 8Gb..

/dev/sda7 is /home for Linux, and /dev/sda8-10 are mounted there to access all the current stuff that I'm using in any particular month or so.  These all come off the 500GB external drives that keep everything handy if I need to grab something I didn't think I'd be needing when I checked out of the last hotel.

/dev/sda/11 is FAT32 so that Windows has a place to keep data.  I can copy data from there to the ext4 partitions or external drives, and transfer anything back to Windows if there was ever a need to do so.  There's also 4.3Gb free on the C: to receive setup.exes and .zip files, which makes it even easier to run between the two operating systems.

It's also only a 160Gb hard disk drive too, so it's setup for fairly slim to moderate code and SWAP (/dev/sda4) and maximum space for data.  You don't need all the extra partitions for /dev/sda8-10, but I like to keep .iso files and .deb files and other people's files on one partition, and my isos and photos and documents and projects on another partition, and mp3s and movies an another partition, so I know what to copy to where and can still remember what I did last night when I wake up the next morning.

---

