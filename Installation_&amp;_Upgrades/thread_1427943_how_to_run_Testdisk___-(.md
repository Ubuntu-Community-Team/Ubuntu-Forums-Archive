---
title: "how to run Testdisk ??  :-("
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-03-12
hello all!

Recently upon running the palimpsest (in my 9.10 KK) test, i was shocked to be informed of some bad sectors on my toshiba laptop's HDD.

i recall someone on this forum once suggested that the most reliable test for checking HDD consistency is the Testdisk application hosted on wikipedia etc.

my problem is this- although i have downloaded Testdisk (through wikipedia) i dont really know what to do with it. i.e. how do i go about generating a report which will tell me the number of bad sectors etc and if they can be isolated.

when i ran the application all i could see were various leads about recovering an already corrupted hard drive or an accidently lost partition.

so all i want to do is for Testdisk to analyse my HDD and tell me how healthy it is. but i can't seem to find the right steps to do this !

thanks!:(:(

---

### Post by Herman on 2010-03-12
Sorry but you have been misinformed, (unless more features have been added to TestDisk that I haven't noticed yet). 
TestDisk is for scanning your hard disk for the first sectors of partitions that may or may not be listed in the partition table and letting the user choose which ones to write to a new partition table.

If you just want to check one partition at a time for bad blocks, you can use the badblocks command.
The badblocks command takes a while to run so it's a good idea to just do one partition at a time, and if you have a large hard disk drive with large partitions, maybe start it at bedtime and let it run while you're asleep.
```
sudo badblocks -sv /dev/sda1 >> badblocks.report
```Where: 'sda1' is the partition you wish to have tested. Change according to information from the 'sudo blkid' command or 'sudo fdisk -lu'.]
This command will write its output the a file named badblocks report, so you can go find that file and open it to see your information. 
No result, (a blank file) is a pass.
If end up with a large file with a long list describing many badblocks would be an indication you probably do have something to worry about, so back up your data and start shopping for a replacement hard disk.
Even a brand new hard disk has a few bad blocks, but new hard disks come with an ample supply of spare blocks they can exchange for any sectors that become 'bad' due to age and wear and tear. It is only when the supply of spares runs out that bad blocks begin to become apparent to the operating system and the user. That's why I recommend replacing your hard drive if the badblocks command returns much of a result.

Here's an alternative to the above command, if you only want to just run a quick test on a small part of your hard disk, (just a sample), to save time
```
sudo badblocks -sv /dev/sda1 10000000
```This one outputs any results in the terminal screen. Again, no news is good news.

---

### Post by ssulaco on 2010-03-12
> **AM_SOS said:**
> 
Recently upon running the palimpsest (in my 9.10 KK) test, i was shocked to be informed of some bad sectors on my toshiba laptop's HDD.

Check this out.....
[http://ubuntuforums.org/showthread.php?t=1305452](http://ubuntuforums.org/showthread.php?t=1305452)

---

### Post by AM_SOS on 2010-03-12
Many thanks Herman and ssulaco for the quick replies !

See i am not really a computer expert, so what i really want to know is how to test my HDD.

When i saw the Palimpsest report, i was quick to believe it because there have been a number of occasions when i have shut down the computer improperly (i.e. due to electricity outages etc). i am told that such practices tend to create bad sectors in the HDD as the head is not able to park itself properly. Is this true ?

So basically i am worried about the health of my internal HDD and would like to know which tests i need to perform to find out if it is ok or not. any suggestions ?

More importantly, if there is are bad sectors etc, how much longer before the HDD conks out ?

thanks,

---

### Post by Herman on 2010-03-12
> **When i saw the Palimpsest report, i was quick to believe it** because there have been a number of occasions when i have shut down the computer improperly (i.e. due to electricity outages etc). i am told that such practices tend to create bad sectors in the HDD as the head is not able to park itself properly. Is this true ?No, that's not exactly right.

The Palimpsest Disk Utility is a nice GUI front-end for smartmontools. 
To put it simple terms, modern hard disk drives have their own little brains, (controllers), and they also have a small flash memory chip containing their programs, (to tell the controller what to do), and there's also some spare flash memory left over where they can record (log) 'events'. An 'event could be an error of some kind, or the hottest and coldest temperature they have ever been run at, number of operating hours, the number bad blocks, spin up time, all kinds of things like that. It's useful for the manufacturer to look at that log if a hard disk is returned under warranty so they can see what went wrong. If it's a defect from the factory, they can take the appropriate steps to rectify the situation, or it could be owner misuse, maybe they need to advise the owner on how to take care of a hard disk drive.
[S.M.A.R.T]("http://en.wikipedia.org/wiki/S.M.A.R.T.") - wikipedia, [Smartmontools]("http://sourceforge.net/apps/trac/smartmontools/wiki") - sourceforge, [Palimpsest Disk Utility Manual]("http://library.gnome.org/users/palimpsest/stable/intro.html.en") - Gnome Documentation Library. 

S.M.A.R.T. monitoring can give us a few pretty good indications about the condition of our hard disk drive and its history. 

What can go wrong with S.M.A.R.T. is when hard disk manufacturers don't want other hard disk manufacturers to be able to spy on their secret recipes for how to make the world's best hard disk. Some of them deliberatly scramble up the S.M.A.R.T. data and then provide their own secret software for reading their particular brand's data.
That means the Palimpsest Disk Utility isn't able to be 100% reliable, it does its best and it's still quite helpful, but it's not the last word in deciding the fate of your hard disk drive. Some brands of hard disks such as Seagate, are well known to display a lot of error messages in a smartmontools reading, but they're perfectly okay.
Also, the badbocks reported by S.M.A.R.T. are the ones that are being swapped out from the reserved area's store of spare bad blocks. A number of bad blocks is to be considered normal here.

---

### Post by Herman on 2010-03-12
> When i saw the Palimpsest report, i was quick to believe it because **there have been a number of occasions when i have shut down the computer improperly** (i.e. due to electricity outages etc). i am told that such practices tend to create bad sectors in the HDD as the head is not able to park itself properly. Is this true ?Shutting down your computer improperly happens to all of us sometimes and that doesn't harm your hard disk drive. 
It isn't good for our file systems though.

Our file systems in simple terms are special areas in our partitions set aside as a place where the operating system, (the kernel), writes down what sectors it's used to store our files, so it can look then back up again later, next time we want to take a look at a particular file.
If the computer is shut down too quickly, the kernel doesn't have time to finish off recording such information and this leaves a mess in the file system. A file system check is usually a good idea after such an event to clean up the file system before the kernel starts trying to use it again.
Actually, there's a lot more to a file system than that, but that should suffice for a very basic explanation I hope.

---

### Post by Herman on 2010-03-12
> When i saw the Palimpsest report, i was quick to believe it because there have been a number of occasions when i have shut down the computer improperly (i.e. due to electricity outages etc).** i am told that such practices tend to create bad sectors in the HDD as the head is not able to park itself properly. Is this true ?**I'm not sure about that but I imagine the hard disk drive's head would be returned by a spring.
I'm still thinking that over and I think I'll need to check up on that.

What I do know is that some hard disk drives have a ramp where the read and write heads controller arm can rest on when that hard disk isn't running.

I replaced a hard disk in a laptop once after somebody lost their temper with a certain proprietary operating system, (I won't name it), and slammed the lid of the laptop down so hard they caused the read-write heads to come in contact with the spinning platters and ruin the hard disk drive. The new hard disk I replaced it with a [Seagate Momentus 320 GB]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=006442b3f64f9110VgnVCM100000f5ee0a0aRCRD") HDD which came with documentation advertising the feature called 'G-Force Protection' which you can read about in data sheets sublinked from the link I gave you above. G-Force Protection is for snapping the controller arm back to the parked position when the hard disk drive senses that the laptop is being dropped. How clever is that? 
Probably wouldn't help if the lid gets slammed again, but my point is, the hard drives controllers can be quite a bit more intelligent than we give them credit for. :D

By the way, I installed Ubuntu in the owner's laptops, dual booting with the other OS because of the requirement for some special accounting software that's popular in this country.

---

### Post by Herman on 2010-03-12
> So basically i am worried about the health of my internal HDD and would like to know which tests i need to perform to find out if it is ok or not. any suggestions ?

More importantly, if there is are bad sectors etc, how much longer before the HDD conks out ?

thanks,Have you tried running the badblocks command I told you about in an earlier post? :D

---

### Post by AM_SOS on 2010-03-13
Hey Herman,
Many thanks for the detailed replies ! Made for a great learning experience. Something which leads to greater independence and general peace of mind. I remember feeling really nice when I formatted and installed XP without needing to take help from PC technicians. Have been hoping to get to the same level with Ubuntu related stuff. Unfortuntately, my research work sort of comes in way.
In fact, though we are not discussing it here - I had at one point wanted to completely shift over to Ubuntu but didn't have the patience ( or the courage ! ) to go through the long re-learning required to use the Open Office Word application ( I have in mind all those shortcuts that one has discovered for MS Word, allowing one to work faster and efficiently ).
Finally, will try and run the badblocks test asap and hopefully get back to you if you don't mind !
Many thanks!

---

