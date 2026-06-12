---
title: "Partitioning problems"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Colo2 on 2009-11-19
Hey. I downloaded the latest kubuntu. It refused to allow me to resize my windows partition to make way for my linux one. I downloaded gparted livecd and tried that, I get an error telling me "it failed to complete the operation" or something. It will not resize ! :(

I've tried defragging multiple times, and chkdsk /f multiple times
same damn problem

any help would be appreciated!
thank you ;)

---

### Post by phillw on 2009-11-19
> **Colo2 said:**
> Hey. I downloaded the latest kubuntu. It refused to allow me to resize my windows partition to make way for my linux one. I downloaded gparted livecd and tried that, I get an error telling me "it failed to complete the operation" or something. It will not resize ! :(

I've tried defragging multiple times, and chkdsk /f multiple times
same damn problem

any help would be appreciated!
thank you ;)

Which version of Win are you using ?
What size hard-drive do you have ?
what partitions do you already have ?
Phill.

---

### Post by Colo2 on 2009-11-19
> **phillw said:**
> Which version of Win are you using ?
What size hard-drive do you have ?
what partitions do you already have ?
Phill.

XP Pro
70 or 80... 80 I think
AFAIK Just the windows one, tho in the partitioner it shows a swap partition as well.

---

### Post by phillw on 2009-11-19
> **Colo2 said:**
> XP Pro
70 or 80... 80 I think
AFAIK Just the windows one, tho in the partitioner it shows a swap partition as well.


Okies ... we may be a bit tight on disk space. How much does windows report as being used / free ?

Phill.

---

### Post by Colo2 on 2009-11-19
Used: 38.6GB
Free: 35.3GB

CAPACITY: 74.0GB

Btw thanks for taking the time to help me :)

---

### Post by phillw on 2009-11-19
> **Colo2 said:**
> Used: 38.6GB
Free: 35.3GB

CAPACITY: 74.0GB

Btw thanks for taking the time to help me :)

Okies.

To 'dip your toe' into Ubuntu, I'd suggest shrinking your windows partitiion by 11GB
That will allow 10GB for Ubuntu and 1GB for swap. Once you decide to keep ubuntu you can always shrink windows some more & grow you ubuntu area.

I'll post back a link with a set of instructions for you ... brb

Phill,
BTW - you're welcome

---

### Post by Colo2 on 2009-11-19
Hey Phill.
Im pretty sure I want ubuntu! :p I've been using it on and off for the past 6 years, you are probably right, 10 GB would be enough. Ill give it a shot and post back with the outcome. thanks for the hand ! ;)

---

### Post by phillw on 2009-11-19
<< back :D

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Will talk you through, with screen-shots, of the slicing etc. for the Ubuntu area. The instructions are for 8.04, but don't worry about that - once the Ubuntu CD get's into it's swing - The important bit is the allowing Ubuntu to re-size .. As I mentioned - use the slider to give you 11GB for ubuntu - don't accept the default of 2.5GB.


Any problems - pop back - I'll keep an eye on the thread.

Regards,

Phill.

---

### Post by Colo2 on 2009-11-19
Same damn error. This is now doubling what windows needs.

I wonder if theres some write protection thing on the disc that windows has put in place?
I dont really know what to try now :(

---

### Post by phillw on 2009-11-19
> **Colo2 said:**
> Same damn error. This is now doubling what windows needs.

I wonder if theres some write protection thing on the disc that windows has put in place?
I dont really know what to try now :(


Okies, let's go back to doing it the manual way ...

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Have a read through the introduction and then head to the resizing bit to shrink your existing partion down ..

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

Phill.

---

### Post by Colo2 on 2009-11-19
[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

thats pretty much what I did. What I am doing has no reason to return errors :(

---

### Post by phillw on 2009-11-19
> **Colo2 said:**
> [http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

thats pretty much what I did. What I am doing has no reason to return errors :(

This is wierd...  This is a possibe ...

can you do an md5 checksum on your koala cd ....

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It'll remove that from the equation.

Phill.

---

### Post by darkod on 2009-11-19
If nothing else works, one option, although not preferred, can be to make image of the XP installation with something like CloneZilla, then with Gparted delete the current partition which is taking up the whole drive, again with Gparted create ntfs partition, image back XP, check if it works at that point, and then continue with the unpatitioned space and kubuntu.
CloneZilla seems to have lots of fans because it comes as bootable CD and when creating the image it saves only the data, not the free space from partitions.
Who knows how windows created the current partition. :) Maybe stuck something on it.

---

### Post by phillw on 2009-11-19
We could well be heading that way soon !!! .. Odd that GP can't successfully shrink his partition, it's been de-fragged & there's plenty of free space.

Phill.

---

### Post by Colo2 on 2009-11-19
> **phillw said:**
> This is wierd...  This is a possibe ...

can you do an md5 checksum on your koala cd ....

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It'll remove that from the equation.

Phill.

I am using a gparted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) :p so I dont think the problem is to do with my Koala CD 

> If nothing else works, one option, although not preferred, can be to make image of the XP installation with something like CloneZilla, then with Gparted delete the current partition which is taking up the whole drive, again with Gparted create ntfs partition, image back XP, check if it works at that point, and then continue with the unpatitioned space and kubuntu.
CloneZilla seems to have lots of fans because it comes as bootable CD and when creating the image it saves only the data, not the free space from partitions.
Who knows how windows created the current partition. Maybe stuck something on it. 

Seems like alot of work :( I may have to resort to that, or maybe Ill just wipe the drive and install linux as the seul OS.

I am still looking for suggestions tho! ;) thank you so much to the people who have helped :)

---

### Post by Colo2 on 2009-11-19
Im'a go to bed now. Ill check the topic for replied tomorrow morning

Thanks again :)

---

### Post by phillw on 2009-11-19
Regardless of what method you choose - md5 checksumming your install CD is always a GOOD idea !!

Phill.

---

### Post by Colo2 on 2009-11-20
Thanks for the help!
I think there may be a problem with my disc, although I doubt that is the only problem. I installed it within windows using wubi by mounting the .iso with Daemon tools and it worked. Whilst trying to install it with the disc, it failed. 

I will eventually go over to linux only, I hate everything to do with windows but sometimes requirements overpower want!

Thanks ;)

---

### Post by Bartender on 2009-11-20
Colo -
Any chance you could find the cash to buy a second HDD?  Is this a desktop?

---

### Post by Colo2 on 2009-11-20
Yeah, this is a desktop, About the hard drive. Well, I am hoping to buy a new PC soon, so I don't really want to spend any more money on this piece of crap :P

Thanks ;0

---

