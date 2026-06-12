---
title: "The changes could not be written to the storage devices"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by Mugabuga on 2010-04-28
I tried to partition my hard drive in half, 35GB for each OS, for dual-booting Ubuntu and XP. When I try to partition the drive, it works for about 5 minutes, then give me and error something like this. 
> An error occurred while writing the changes to the storage devices. The operation has been aborted.
Is there any way to fix this, or do I have to just use XP?

---

### Post by Herman on 2010-04-28
I recommend running a thorough file system check in Windows before resizing the partition, GParted doesn't care about fragmentation, but if the file system is a wee bit corrupted if might bail up on you. 
Go to 'My Computer', and right-click on Drive C:. click properties and click the tools tab, then schedule a file system check for next time you reboot, and make it a good one.
Alternatively, you could run CHKDSK /R from a Windows XP 'Installation CD, from the 'Recovery Console'.
The reason for this is that Windows may sometimes tolerate small file system problems and many Windows users are accustomed to frequent defrags, but for some strange reason are frightened of file system checks. File system checks are a good thing and should be done regularly to keep the file system healthy. :)

Otherwise, you could have something wrong like a speck of dust on your optical drive lense, or a fingerprint on your CD, or a bad burn or any of a number of other minor annoyances. 

Try using a [Parted Magic]("http://partedmagic.com/") Live CD  or USB to pre-partition your drive with and see if you still get errors. Parted Magic is free and it's extremely useful and comes with a lot of other great software, including Super Grub Disk 1 and 2.

If you still have trouble, try making a Ubuntu Live USB, because USB drives are faster than CD drives and are not subject to the same problems.

You could try checking the md5sum of your downloaded .iso to make sure it's not corrupted too, that's another thing to look at maybe, 

[Why  integrity check your downloaded .iso?]("http://members.iinet.net.au/%7Eherman546/p17.html#Why_integrity_check_your_downloaded_.iso")

[Checking  the integrity of your .iso from a Linux live CD]("http://members.iinet.net.au/%7Eherman546/p17.html#Checking_the_integrity_of_your_.iso_from_a_Linux_live_CD")
                       [               Checking the integrity of your .iso in Windows]("http://members.iinet.net.au/%7Eherman546/p17.html#Checking_the_integrity_of_your_.iso_in_Windows")

---

### Post by Mugabuga on 2010-04-28
I did a Disk Check, and the information was too fast for me too read. And the bootable USB drive won't work on my computer. The check integrity option on the Ubuntu Live CD said it was OK. Any other workarounds?
EDIT: I think the new 10.04 will work.

---

### Post by Mugabuga on 2010-04-29
AAARRGH! I just downloaded the 10.04 Live CD and it still won't install. Is it possible theres a problem with my hard drive? :confused:

---

### Post by Herman on 2010-04-29
There could be but there might also be any one of dozens of other possible problems. 

I had some problems with one of the computers I use too, it has a puzzling problem with the CD drive recognizing some CDs and not others, for no apparent rhyme or reason I have been able to deduce so far. My new Lucid CD booted but froze at setting up the clock in the first installation attempt, then it got a little further before stopping on the next attempt, and the third time I was lucky and was able to complete an installation. It's a new CD/DVD drive, but there's something funny about it that this motherboard doesn't seem to like, I'm not sure. Most of the time things go okay for me.

Hard disk drives are another problem, Ubuntu comes with 'Disk Utility' to read the hard disk's memory logs, and it does give some indication but is to be taken with a grain of salt, especially with some brands of hard disks. The badblocks command is always reliable, as far as I know.

I have found it sometimes helps to check jumper settings and cables, sometimes to the extent of dismantling a machine and re-assembling it again. 
A friend of mine has a computer and it wouldn't recognize his SATA DVD drive. I went to the trouble of flashing his PC's BIOS for him which turned out to be way more complicated than I thought, (long, long story). In the end, the simple act of swapping the two SATA cables turned out to fix the problem. There's no scientific explanation for that that I can think of. 'Go figure' , as they say.  Computers can be weird.

---

### Post by Mugabuga on 2010-04-29
> **Herman said:**
> 

Try using a [Parted Magic]("http://partedmagic.com/") Live CD  or USB to pre-partition your drive with and see if you still get errors. Parted Magic is free and it's extremely useful and comes with a lot of other great software, including Super Grub Disk 1 and 2.
So if I were to use Parted Magic, would there be a tutorial for this?

---

