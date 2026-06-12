---
title: "Uninstalled Unbuntu, and now hard drive cannot be used as primary only secondary."
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by foobaka on 2010-11-27
these posts are from another thread i posted in, that thread was a bit dead so i making a new thread in hopes to resolve problem. 


basically uh, i have a netbook with ubuntu 10.10 installed on it, i  recently used BootIt NG to attempt to clear the ubuntu partitions on it.  

though, now i'm clueless as to how to set the file system up for a  harddrive [initial intent is to make it for a windows xp OS]. i've tried  creating a 11/bh fat32 and a 7/7bh ntfs but had no luck. when i was booting  windows xp from cddrom drive, it inspects drivers and such but next comes to  a screen where it says, 'setup did not find any hard disk drives  installed in your computer'. i think the harddrive may need to be  reconfigured. 
~ thanks in advance, foo. 

> 
User: Jammanuser

Interesting. 
I'm going to need more info:

1. You said you used Bootit NG to "attempt" to clear the ubuntu partitions on your netbook. Does that mean it failed?
2. Please explain the layout of your system (i.e. how many hard drives  you have connected and/or inside your netbook, how many partitions on  each HDD, etc.). 
3. When you used BootIt NG, I'm assuming you used it directly from the CD and did not install it to your hard drive? 
4. If BING succeeded in wiping Ubuntu off of your system, is there any  other OS on there at the moment (in other words, were you multibooting  before removing Ubuntu)?
5. Please give a detailed description of the procedure you did with  BING, not just simply say that you attempted to wipe the Ubuntu  partitions with it. Since BING is a powerful program, and has many  features, not just the ability to wipe a partition, I want to know what  else you may have done with BING, if anything. I also want to know if  you deleted the partition(s) or if you just reformatted them.

That will give me a fairly good idea of your situation, and may help me help you solve your problem. :wink:  Keep in mind that if there are no partitions left on your computer, you  can always use BING from the CD to create one, format it as FAT 32, and  then you'll be able to install Windows XP onto it.

Cheers.
My response to his post:

> 
User: Jammanuser
1. You said you used Bootit NG to "attempt" to clear the ubuntu partitions on your netbook. Does that mean it failed?
#01.
well, i used it to clear the ubuntu partitions, and successfully did clear them, however i may have deleted ones that i shouldn't have? i don't know. there were 4 or 5 entries being Linux and linux native in the Partition_Work menu when i launched BootIt NG. i thought i just had to clear them all and then just create a new entry for windows ntfs. after clearing those, i've been attempting to re-create a single entry that's ntfs partition and thus the windows installation screen unsuccessful follows.


> 
User: Jammanuser
2. Please explain the layout of your system (i.e. how many hard drives you have connected and/or inside your netbook, how many partitions on each HDD, etc.).
#02.
the layout of the system is: it has (1) SATA 160GB internal as primary. it used to have 4 or 5 partitions, but currently only 1, and i intend to have only 1, i just wanted windows partition. in bios though, it does not show the hard drive at all. strangely enough, i've come across this second netbook that does not display hard drive information in bios.

the netbook Specifications:
Brand: HP Mini
Model: 311-1000 NR
Processor Type: Intel (R) Atom(TM) CPUN270 @ 1.60GHz
Processor Speed: 1600 Mhz
Total Memory 1024 MB
Hard Drive: SATA 160GB Internal
Cd-Rom Drive: No


> 
User: Jammanuser
3. When you used BootIt NG, I'm assuming you used it directly from the CD and did not install it to your hard drive?
#03.
the netbook i have does not have a cdrom drive, so i used a 2GB USB drive to run the BootIt NG off of, and i did not install it [read couple times in many places that they said you shouldn't try to install it on your hard drive whether they mean hard drive or usb i assumed it was the same in this case]. and the method i use to install windows is that: since netbook does not have a cdrom drive, i use a usb to ide adapter and connected a ide cdrom drive into the usb port and run the windows installation cd from there [works perfectly fine, i've used and tested this method hundreds of times.]


> 
User: Jammanuser
4. If BING succeeded in wiping Ubuntu off of your system, is there any other OS on there at the moment (in other words, were you multibooting before removing Ubuntu)?
#04.
there are no OS's on there at the moment, only a partition that i keep re-creating in hope that windows installation setup would work. the question of 'was i multi-booting', i cannot answer that since my friend bought it from someone but then he sold it cheap for to me since he said he had linux installed on it and he didn't want to go to the hassle of uninstalling linux and putting windows back.


> 
User: Jammanuser
5. Please give a detailed description of the procedure you did with BING, not just simply say that you attempted to wipe the Ubuntu partitions with it. Since BING is a powerful program, and has many features, not just the ability to wipe a partition, I want to know what else you may have done with BING, if anything. I also want to know if you deleted the partition(s) or if you just reformatted them.
#05.
well, on my PC, i downloaded bootit ng and made it to be bootable on usb drive. now, the netbook initially had ubuntu 10.10 netbook edition on it. so after booting up with the usb drive, it launched bootit ng, the screen that popped up was the Parition_Work. in there, there were about 4 or 5 MBR entries listed, majority being Linux or Linux Native. so i clicked Delete on all the entries. after i cleared all, i created a new entry called, 'MBR Entry 0' and made the File System: 7/7h HPFS/NTFS and under additional information it said Bootable: NTFS and Cluster Size as 4096 bytes. after that, i clicked View MBR and clicked Set Active and Std MBR, and clicked Apply. afterwards, i clicked close, and rebooted the netbook with the USB to IDE adapter plugged in and launched the setup for windows. i've tried 3 different windows XP install discs, none worked either.

it went to this screen first:
[http://i.imgur.com/4oTGj.png](http://i.imgur.com/4oTGj.png)

then it went to this screen:
[http://imgur.com/9uvrS.png](http://imgur.com/9uvrS.png)

and with a different windows installation cd,
it went to the first screen then this screen:
[http://i.imgur.com/eTSNB.png](http://i.imgur.com/eTSNB.png)

it kept doing that and so each time i tried something new and created a new MBR Entry after deleting the old entry that did not work, and this time used a different File System like for example: to 11/Bh: FAT-32 and so forth.

couple um notes, i have not reformated the hard drive yet though only deleted partitions after creating and deleting.

currently i created MBR ENTRY 0 and this is the screen shots for View MBR and Properties of the Entry.
[http://imgur.com/XkcSj.jpg](http://imgur.com/XkcSj.jpg)
[http://imgur.com/gexhY.jpg](http://imgur.com/gexhY.jpg)

also, i am able to unplug the SATA hard drive and plug it into my desktop as secondary / slave. the only folder that was on the hard drive was, 'System Volume Information'. so basically the hard drive can be read as a storage device but currently NOT as a primary hard drive. [i think the MBR is either corrupted / incomplete / and or invalid due to my idiocy]. 

again, the basic outline of this whole ordeal i would like to highlight is, ***"so basically the hard drive can be read as a storage device on another PC but  currently CANNOT be used as a primary hard drive in a netbook and or desktop PC. i think the MBR is either  corrupted / incomplete / and or invalid"***

and, at some point, after plugging the hard drive as secondary in my dekstop pc, i ran TestDisk 6.1. and after a deep search it did find the deleted linux partitions but it said it wasn't recoverable anymore [i do not know why i had ran that or what my intent was].

thanks again!!! =P
~ foo

---

### Post by Wobblybob on 2010-11-27
It's been awhile since i used XP but from what I remember the install disk has no SATA drivers on it so if your HD is SATA you need to [a] find the drivers and [b] look out for the Press F whatever option to load raid drivers option on XP installer then it will ask for a floppy holding the drivers. With a netbook you will have a problem at this point. If you have a usb floppy drive your in luck if not you could try slipstreaming the drivers using nlite [it's free and available on net].

good luck!

---

### Post by foobaka on 2010-11-28
hi, um i've read somewhere, where i can emulate a usb-drive as a floppy drive, so that part might / is taken care of maybe, i don't exactly know where either. 

so, now the issue becomes finding the drivers and pressing F for the option to load the drivers. my main question is what type of driver am i suppose to look for? [in my case, the install disc says press F6, then it loads a series of drivers, and then says insert the disk with raid drivers and or press F3 to quit / continue.]



[http://imgur.com/X8euZ.jpg](http://imgur.com/X8euZ.jpg)
here is a picture of a custom windows disc i use: 

[http://imgur.com/iiJ9G.jpg](http://imgur.com/iiJ9G.jpg)
here is a picture of the setup saying cannot find harddrive / configured incorectly and or just none found along with 3 choices 1 being specifying a device using i suppose raid since going into that screen gives a list of drivers of raid, 2- continueing will give me the option of loading my own raid from floppy drive, and 3 to quit. normally when i do this way i don't get this screen where it says hard drive cannot be found when i install windows on desktop PCs using IDE harddrives and sometimes even SATA harddrives as primary harddrives but for some reason netbook's SATA is being an issue when trying to install as primary. 

[http://imgur.com/Wx9Rr.jpg](http://imgur.com/Wx9Rr.jpg)
here i have a picture of pre-set raid drivers that came with the XP sp3 install disc, in that box there's at least 50-60 entries in there. am i allowed to pick any random one? or does it have to be a specific accordingly to the hard drive?

and is it possible to exemplify and or describe this slipstreaming and nlite methodology? 

so, overall, my 3 questions are: 01- what type of raid drivers should i look for / good places to find them, 02- some sort of quick instructions on this process, and 03- this slipstreaming / nlite ordeal, don't know much about it

---

### Post by wet-willy on 2010-11-28
You'll have to get hardware details for the netbook. I don't think many if any came with XP, hardware in netbooks may not have XP drivers. Go to the mother board manufacturer's site as the controller is part of the chipset.
No need to keep recreating the partition, if bootitng sees the drive and is able to create without error means it's good to go, just XP is not.
I just finished using Nlite an hour ago to remove the OEM pre-install from my Dell XP Home SP2, integrated SP3 and changed the key to match the one on the sticker of the HP desktop I found at the dump today, it's surprising what people throw away, nice unit, had everything in good shape, just don't want the Compaq bloat-ware system it has.

Just make an empty folder in a running Windows unit and slide in your CD, install and run nlite and it will ask for the source files, direct it to the CD, then direct the destination to the folder you created, select from an easy menu what changes you want to make, for instance "integrate drivers", or "unattended install" where you can remove OEM pre-install stuff, create your user, set time zone, etc....Just play with it, you might make a few new ISOs before you figure out how to design it to your liking. Select everything and go through it and just hit next to avoid changes, and you'll see what's what.

---

### Post by Wobblybob on 2010-11-28
Looks like you need to do some research on the netbook makers site to find the SATA drivers or motherboard site if that fails then start googling for netbook model to see if someone has uploaded them. Why did you remove Ubuntu by the way?

---

### Post by foobaka on 2010-11-28
ah those kinds, ok i'll start looking for them then. and, i needed a removal of ubuntu since i will be selling the netbook soon, since i got cheap, i thought might as well resell it after i put in a little work i suppose. i mean i could have multi-boot in the end but i just had the 'make it windows only' idea in my head at that time.

---

