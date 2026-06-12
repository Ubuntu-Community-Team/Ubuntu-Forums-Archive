---
title: "Will Jaunty be doing away with swap partitions?"
date: 2008-12-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-12-22
Just curious.

---

### Post by a fenderson on 2008-12-22
Why would it?

---

### Post by klange on 2008-12-22
No...
Will you be doing away with your arms?

---

### Post by plun on 2008-12-22
No I dont think so but I haven't used a swap on a partition for years !

I am using a dynamic swap....

[http://www.debian-administration.org/articles/550](http://www.debian-administration.org/articles/550)

---

### Post by Starks on 2008-12-22
Unless Ubiquity is broken further than what I have indicated in previous posts, it would seem that swap partitions will not be created by default.

Is this not the case?

---

### Post by plun on 2008-12-22
> **Starks said:**
> Unless Ubiquity is broken further than what I have indicated in previous posts, it would seem that swap partitions will not be created by default.

Is this not the case?

Nope it will probably not...  but you can also use the alternate CD as Bou wrote.

It takes a little time understanding how it works with a text based installer but the priciple is exactly the same as with Ubiquity,

Watch out for formats.... 8-)

and you will learn something new  :)

---

### Post by gnomeuser on 2008-12-22
For SSD based machines you shouldn't use swap (wears the flash unneededly), aside that I think they are here to stay. In time as we do away with harddrive based devices we might see them disappear but in the Jaunty timeframe expect swap to be there.

---

### Post by Starks on 2008-12-22
I really want to rage at the Ubiquity devs for messing around with the partitioning code in Jaunty.

---

### Post by Gina on 2008-12-22
> **gnomeuser said:**
> For SSD based machines you shouldn't use swap (wears the flash unneededly), aside that I think they are here to stay. In time as we do away with harddrive based devices we might see them disappear but in the Jaunty timeframe expect swap to be there.I was under the impression that flash drives were solid state and had no moving parts and therefore didn't wear out :confused:

---

### Post by gnomeuser on 2008-12-22
> **Gina said:**
> I was under the impression that flash drives were solid state and had no moving parts and therefore didn't wear out :confused:

[http://en.wikipedia.org/wiki/Solid-state_drive#Disadvantages](http://en.wikipedia.org/wiki/Solid-state_drive#Disadvantages)

Take something like the Hybrid drives Microsoft were so fond of during the Vista development cycle. While they do increase performance dramatically, estimates are that normal use would take 6-12 to wear out the flash component.

This is why installing a common Linux on SSD machines should not be done unless you are really familiar with ways to avoid wearing the SSD out. This includes not using journaling, handling log files differently (say in a ramfs partition or something). If not you might kill the flash component in a year. 

That being said, technology is improving greatly, this may not be a problem worth considering soon. I hear the next generation SSDs have much higher write cycle tolerance.

---

### Post by gradedcheese on 2008-12-22
> This is why installing a common Linux on SSD machines should not be done unless you are really familiar with ways to avoid wearing the SSD out. This includes not using journaling, handling log files differently (say in a ramfs partition or something). If not you might kill the flash component in a year.

That's not really correct.  An SSD has a fairly sophisticated controller that abstracts away the Flash memory and appears to the OS/interface like a normal hard disk.  Internally, the controller does a ton of error correction and wear-leveling in a similar (but much improved) way to how in-Flash file systems were designed.

There's nothing seriously wrong with using an SSD in the same way that you'd use a traditional hard disk, though not using journaling (ie: ext2 instead of ext3 rootfs) would help.  You're not going to kill the Flash in a year, if you do then your SSD controller is junk or otherwise not doing its job.

---

### Post by gnomeuser on 2008-12-22
> **gradedcheese said:**
> That's not really correct.  An SSD has a fairly sophisticated controller that abstracts away the Flash memory and appears to the OS/interface like a normal hard disk.  Internally, the controller does a ton of error correction and wear-leveling in a similar (but much improved) way to how in-Flash file systems were designed.

There's nothing seriously wrong with using an SSD in the same way that you'd use a traditional hard disk, though not using journaling (ie: ext2 instead of ext3 rootfs) would help.  You're not going to kill the Flash in a year, if you do then your SSD controller is junk or otherwise not doing its job.

that strangely is not what my sources are telling me:

[http://kernelslacker.livejournal.com/132087.html](http://kernelslacker.livejournal.com/132087.html)
[http://valhenson.livejournal.com/25228.html](http://valhenson.livejournal.com/25228.html)

The controller doesn't do nearly as good a job as you would think, though they are getting better. We also need to do better with our filesystem code, our current code isn't written with flash in mind and will affect the wearing of the drive. 

SSDs are still young, care needs to be taken. They are improving quickly though and prices are becoming attractive enough for everyone to play with them. I am hopeful.

---

### Post by Gina on 2008-12-23
Interesting...  Think I'll have to do some searching sometime to find out what the mechanism of SSD is and why a seemingly semiconductor process should have a wearing-out mechanism.

I was thinking of buying a netbook with SSD for the silence and reliability aspects but now it seem the latter is a fallacy.  Hard drive ones are cheaper but I doubt would be any advantage to me over my laptop except for being smaller and lighter (this was not my main concern).  Disappointing :(

Thank you for putting me right *gnomeuser* :)

---

### Post by skirkpatrick on 2008-12-23
I'm an embedded systems developer and have dealt with flash memory for years.  Flash memory wears out when it is erased, not when it is written.  The data sheets all tell you how many erase cycles it supports.  You can erase an entire block (block size depends on size of the flash chip, anywhere from 64MB to 128MB usually) which sets the bits to a value of '1'.  You can then write to the block which actually clears bits to a '0' when required.  The reason that flash memory wears out is because the semiconductor gates will get to the point that they will no longer reliably hold an electrical charge.  Wear-leveling algorithms try to spread usage across the whole device instead of performing all operations say in the first couple of blocks.  Some wear-leveling will even try to work around bad sections of memory, similar to how your hard drive marks and avoids bad sectors.

---

### Post by gnomeuser on 2008-12-23
> **skirkpatrick said:**
> I'm an embedded systems developer and have dealt with flash memory for years.  Flash memory wears out when it is erased, not when it is written.  The data sheets all tell you how many erase cycles it supports.  You can erase an entire block (block size depends on size of the flash chip, anywhere from 64MB to 128MB usually) which sets the bits to a value of '1'.  You can then write to the block which actually clears bits to a '0' when required.  The reason that flash memory wears out is because the semiconductor gates will get to the point that they will no longer reliably hold an electrical charge.  Wear-leveling algorithms try to spread usage across the whole device instead of performing all operations say in the first couple of blocks.  Some wear-leveling will even try to work around bad sections of memory, similar to how your hard drive marks and avoids bad sectors.

Now admittedly I am not a huge expert on filesystems nor flash technology but it seems to me that we do a lot of file erasing in Linux. Just take an area like log files or lock files, without clever wear levelling those are danger areas as far as my research is able to show.

My point though still stands, these are not harddrives, before a bog standard Linux such as Ubuntu can be safely and effectively installed we'd need the installer to contain some logic to detect the use of SSDs and set the defaults accordingly.

---

### Post by quickshade on 2008-12-23
> **gnomeuser said:**
> My point though still stands, these are not harddrives, before a bog standard Linux such as Ubuntu can be safely and effectively installed we'd need the installer to contain some logic to detect the use of SSDs and set the defaults accordingly.

I agree with this, as more and more people switch I think the installer should at least detect the SSD's and configure it properly, although linus just said that intel gave him one of their new SSD drives and he was really impressed, and even was told that intel has cut wear and tear on the device by 50%.

---

### Post by gradedcheese on 2008-12-23
> My point though still stands, these are not harddrives, before a bog standard Linux such as Ubuntu can be safely and effectively installed we'd need the installer to contain some logic to detect the use of SSDs and set the defaults accordingly.

Out of curiosity, what would you have it do?  I suppose setting noatime would be useful, but unfortunately someone will complain because it's needed for POSIX compliance.  I'm not sure what else the installer would need to configure.  Despite the way NAND Flash wears, an SSD should last about as much as a hard disk.  I'm speaking from some experience here with NAND Flash, file systems, etc and I'm an embedded systems developer.  Please do some more reading before just repeating what you see on someone's blog, otherwise you get things like:

> I was thinking of buying a netbook with SSD for the silence and reliability aspects but now it seem the latter is a fallacy.

...really?  I'd say laptop hard disks fail quite a lot due to impact from dropping the laptop, carrying it around while the disk is accessed, etc.  A lot of the accelerometer-based disk head 'parking' systems don't work in Linux by default, probably making it worse.  An SSD is going to be very reliable and its controller will ensure wear leveling of the Flash.  I'd be quite surprised to see a laptop hard disk outlast one under typical use, even with a "stock" desktop Linux installed.

---

### Post by plun on 2008-12-23
> **gradedcheese said:**
> ...really?  I'd say laptop hard disks fail quite a lot due to impact from dropping the laptop, carrying it around while the disk is accessed, etc.  A lot of the accelerometer-based disk head 'parking' systems don't work in Linux by default, probably making it worse.  An SSD is going to be very reliable and its controller will ensure wear leveling of the Flash.  I'd be quite surprised to see a laptop hard disk outlast one under typical use, even with a "stock" desktop Linux installed.

Well.. I am 100% sure that safe SSD is coming within the 2.6.29 kernel.

Please read Linus own blog testing Intel SSD... despite of Intels "Rule the world" manner.

[http://torvalds-family.blogspot.com/2008/10/so-i-got-one-of-new-intel-ssds.html](http://torvalds-family.blogspot.com/2008/10/so-i-got-one-of-new-intel-ssds.html)

----

---

### Post by Gina on 2008-12-23
Thank you *[I]gradedcheese*[/I] for that :)  Have to say I was astonished to be told that a solid state drive had a shorter life than a mechanical spinning disc with a magnetic coating!  Particularly in a portable machine likely to get far rougher use than a desktop.

I shall be watching this with great interest.

---

### Post by plun on 2008-12-23
> **Gina said:**
> Thank you *[I]gradedcheese*[/I] for that :)  Have to say I was astonished to be told that a solid state drive had a shorter life than a mechanical spinning disc with a magnetic coating!  Particularly in a portable machine likely to get far rougher use than a desktop.

I shall be watching this with great interest.

Nope... that is heavily discussed among experts.
Also some FUD about it.

Intel got a new technology...   Linus blog..

Data rescue from a SSD-disk is also something which is important.

---

### Post by Slug71 on 2008-12-23
Well from what i read about SSDs on wikipedia which i know isn't always very true, id still stick with a regular HDD for a couple of years. 

SSDs IMO just are not ready yet.

---

### Post by quickshade on 2008-12-23
It seems the new linux file system Btrfs will have better support for SSD's and will use them way better.

---

### Post by skeetre on 2008-12-24
According to Intel, about their 80 and 160gb ssd 
> Life expectancy  1.2 million hours Mean Time Before Failure (MTBF) 

And their 32 and 64gb ssd
> Life expectancy  2 Million Hours Mean Time Before Failure (MTBF) [http://www.intel.com/design/flash/nand/extreme/index.htm]("http://www.intel.com/design/flash/nand/extreme/index.htm")

Not sure under what usage levels, but that's 136 YEARS.

Either way, I think no matter how you use the ssd drive, it will out last a pata/sata drive with moving heads. Plus... like me the other day, when I tripped on the cords for my 1TB External drive and killed it (click click click), that wouldn't be an issue with the ssd drive. Yes, price is high and space is low, but Toshiba just launched a 512gb ssd drive [Pricing in sample quantities ranges from $220 for the 64GB drive to $1,652 for the 512GB drive]("http://news.cnet.com/8301-1001_3-10125861-92.html") So yeah, price still has to come down.

---

### Post by RAOF on 2008-12-24
> **skeetre said:**
> ...
Either way, I think no matter how you use the ssd drive, it will out last a pata/sata drive with moving heads. 
...

Except that's *just not the case*.  The ability to store a charge degrades significantly with repeated write cycles in flash memory, much moreso than the ability to re-align the magnetic domain in the HDD platter.

New flash (particularly expensive SLC flash) is much, much better than very early flash, which would wear out after only thousands of write cycles IIRC.  Still, the wear characteristics of flash are different to the wear characteristics of magnetic platter drives - you can easily come up with loads that SSDs will fail on first, just as the solid-state nature of flash gives advantages with moving and shocks and such.

---

### Post by ronacc on 2008-12-24
right now its "you pay your money and pick your poison" . For the intended use of netbooks (extreme portability) SSD's are a good choice , for desktops or "fullsize" laptops probably not. Prices are comming down and capacity is going up and read/write cycles will improve so the situation will change . I was around when 20 megabytes was a "huge" harddrive and cost a few 100 $ and ram was measured in kilobytes and quite pricey.

---

### Post by philinux on 2008-12-24
> **plun said:**
> No I dont think so but I haven't used a swap on a partition for years !

I am using a dynamic swap....

[http://www.debian-administration.org/articles/550](http://www.debian-administration.org/articles/550)

Hey like relatively unknown. How come this has not been discussed before.

---

### Post by psycosmyth on 2008-12-24
You guys picked my brain. I have been curious about SSD's replacing RAM entirely by using dedicated swap. This could change the dynamics of microprocessor development forever. I do not see an end to swap any time soon.

---

### Post by gnomeuser on 2008-12-24
> **ronacc said:**
> right now its "you pay your money and pick your poison" . For the intended use of netbooks (extreme portability) SSD's are a good choice , for desktops or "fullsize" laptops probably not. Prices are comming down and capacity is going up and read/write cycles will improve so the situation will change . I was around when 20 megabytes was a "huge" harddrive and cost a few 100 $ and ram was measured in kilobytes and quite pricey.

No man now you made me all nostalgic, my first machine was the second i386 to get to Denmark. 16Mhz, 20megs of harddrive, 2 megs of ram. That thing was a beast. If it wasn't for the old lady demanding that my dad and I threw it out, it would still be running today. Extremely sturdy machine, they just don't build them like that anymore.

Ah these youngsters, sometimes I think they are missing out on all the fun we had discovering computing.

---

### Post by Gina on 2008-12-24
Ah yes indeed!!  I have seen computers develop from mainframes and minis using punched cards and paper tape to what we have today.  Very interesting.

---

### Post by autocrosser on 2008-12-24
Yes--remember teletype port systems??? Was using a HP mainframe with 10 ports scattered around--kept rolled up tapes to input programs....Good-old HP basic--I was goto-ing everything :)  Was talking to a friend last night at a party & remembering about the late 60's at MIT--fun times then--a whole room has less computing power than one new netbook :)

Mag drum drives--anyone?

---

### Post by Gina on 2008-12-24
Yes, I've used a teletype connected by telephone line to a mainframe at one of the universities.  And yes, programs typed onto paper tape - sent when you have a slot allocated, then you get the results back next time you have a slot :lol:  Very slow process!!  As I recall, the first language I used was Mercury Autocode (bit like basic).  That was in the early 60's.  I've used several programming languages including basic, algol, fortran, pascal, cobol, and various assemblers for a number of different processors.

I wish I was a bit younger and still capable but I find operating system programming a bit much for me these days - I stick to relatively simple scripting - or I'd love to get really involved in Ubuntu development.

---

### Post by ronacc on 2008-12-24
I actualy ran across a roll of punchtape with HP basic on it from an HP2100 mini we had where I worked circa 1972 , I hadn't looked in that box since I moved 30 years ago , I remember scotch taping torn tapes back together and repuncing the holes under the scotch tape with an awl to get it through the reader 1 more time to dupe it , now that was data recovery !

---

### Post by Gina on 2008-12-24
I've actually produced a boot loader on a punched tape by hand - making holes for each and every bit (forming one byte across the tape) using a hand punch. The boot sequence was only a dozen or so bytes long, fortunately.  I don't think you can get much more basic than that :lolflag:

I have also repaired broken paper tape with scotch tape and repunched holes with the hole punch.

---

### Post by autocrosser on 2008-12-25
Hey Sherman---crank up the "Way-back machine" :lolflag:

---

### Post by Greyed on 2008-12-25
> **a fenderson said:**
> Why would it?

Swap partitions provide very little advantage over swap files these days.  Originally there was a distinct difference between accessing the swap file on a bare partition and accessing the swap file with the file system overhead.  Nowadays, for most purposes, the two are pretty identical.  Strictly speaking, when you're hitting swap you're already taking a huge performance hit from access measured in ns to access measured in ms to seconds.  Adding a nominal ms or two of file system access on top of that doesn't matter.

This is especially true when the machine is a VM which is increasingly common in the one area where shaving a few ms of access time off hitting swap might still be worth agonizing over; servers.

> **WindowsSucks said:**
> No...
Will you be doing away with your arms?

Don't be a prick.  Just because you don't understand the issue being discussed doesn't mean you need to express it by belittling others.

---

### Post by Greyed on 2008-12-25
> **gradedcheese said:**
> I suppose setting noatime would be useful, but unfortunately someone will complain because it's needed for POSIX compliance.

Yay!  The reason I started my blog comes to fruition in less than a month!  :guitar:  That reason being to collect my often-repeated essays regarding topics of interest to me.  Instead of re-writing them dozens of times, write once and link!

[No time like noatime]("http://greydmiyu.wordpress.com/2008/12/03/no-time-like-noatime/") - why noatime isn't a good thing any more.

---

### Post by gradedcheese on 2008-12-25
Sweet, I didn't notice that Ubuntu now mounts with relatime set.  That's one less thing to worry about then.

---

### Post by plun on 2008-12-25
> **philinux said:**
> Hey like relatively unknown. How come this has not been discussed before.

[http://www.debian-administration.org/articles/550](http://www.debian-administration.org/articles/550)

Well... it was 2006-2007, no idea why this wasn't further discussed ?

I cannot see any meaning with a fixed swap but one disadvantage with a file swap is encryption

Ubuntus package
[http://packages.ubuntu.com/jaunty/dphys-swapfile](http://packages.ubuntu.com/jaunty/dphys-swapfile)


Found an article about it:
[http://ubuntumagnet.com/2007/10/reasons-choose-swap-files-over-swap-partitions](http://ubuntumagnet.com/2007/10/reasons-choose-swap-files-over-swap-partitions)

A swap-file has never failed for me...:)

---

### Post by ShirishAg75 on 2008-12-25
There need to be some sort of benchmarking or something. The only advantage I see is unlike partition you can change swap file on the fly. At installation time how can one do that is something which needs to be put about.

---

### Post by plun on 2008-12-25
> **ShirishAg75 said:**
> There need to be some sort of benchmarking or something. The only advantage I see is unlike partition you can change swap file on the fly. At installation time how can one do that is something which needs to be put about.

Nope, I cannot find any good ones....

Another way using an encrypted swap-file
[http://ubuntumagnet.com/2007/11/creating-encrypted-swap-file-ubuntu-using-cryptsetup](http://ubuntumagnet.com/2007/11/creating-encrypted-swap-file-ubuntu-using-cryptsetup)

But I don't have any secrets within my PC....;)


SSD Myths and Legends...
[http://www.storagesearch.com/ssdmyths-endurance.html](http://www.storagesearch.com/ssdmyths-endurance.html)


Nevertheless I cannot see any reason for a fixed swap partition...must be something from the stone-age...:)

---

### Post by gnomeuser on 2008-12-25
> **plun said:**
> Nope, I cannot find any good ones....

Another way using an encrypted swap-file
[http://ubuntumagnet.com/2007/11/creating-encrypted-swap-file-ubuntu-using-cryptsetup](http://ubuntumagnet.com/2007/11/creating-encrypted-swap-file-ubuntu-using-cryptsetup)

But I don't have any secrets within my PC....;)


Excellent, can I have your passwords then? Vacation photos, credit card numbers, sensitive work information.. people store all kinds of things in caches without knowing it. I think we should take this a bit more seriously and start doing security by default rather than opt-in.

---

### Post by ronacc on 2008-12-25
the amount of security ( if any) required should be left up to the user , at what point do we cease trying to protect people from themselves ? Give them the tools and a clear explantions of how when and why they should use them and then let them decide , I am not my brothers keeper , his friend , helper and advisor perhaps but I do not "own" him .

---

### Post by Greyed on 2008-12-25
> **ronacc said:**
> the amount of security ( if any) required should be left up to the user , at what point do we cease trying to protect people from themselves ?

I have a couple of botnets that say otherwise.

---

### Post by ronacc on 2008-12-25
My default position is always freedom of individual choice. I deeply resent someone ( or entity) assuming that they have the "right" to make my personal decissions for me and I in turn do not assume that I have the right to do it for others ( with the obvious exceptions of young children and truly incompetent adults ).

---

### Post by Greyed on 2008-12-25
> **ronacc said:**
> My default position is always freedom of individual choice. I deeply resent someone ( or entity) assuming that they have the "right" to make my personal decissions for me and I in turn do not assume that I have the right to do it for others ( with the obvious exceptions of young children and truly incompetent adults ).

As is mine, look at my blog.  But tell me, setting the default swap to encrypted prevents a person from the choice of switching it to unencrypted how, exactly?  :P

---

### Post by ronacc on 2008-12-25
it does not prevent switching back but my way would be to ask at install time .

---

### Post by gnomeuser on 2008-12-25
> **ronacc said:**
> it does not prevent switching back but my way would be to ask at install time .

"Encryption ensures that your data remains private in the event of theft, the default is to have this enabled for your protection. If you forget the password there is no way to retrieve your data. Please uncheck the box if you want to disable encryption"

[X]

Default to a secure setup and let the user opt-out. You do not default to selling a house without locks on the doors either but if people don't like them they are free to ignore security and leave them unutilized.

---

### Post by vade on 2008-12-25
How does file system en/decryption affect performance? Is the difference to non-encrypted noticeable?

---

### Post by MacUntu on 2008-12-25
> **ronacc said:**
> assuming that they have the "right" to make my personal decissions for me
> **gnomeuser said:**
> Default to a secure setup and let the user opt-out. You do not default to selling a house without locks on the doors either but if people don't like them they are free to ignore security and leave them unutilized.

Making decisions requires knowledge. Users are not dumb but you can't expect John Q. Public to know enough about every option an expert would like to see during the install process. There needs to be a set of reasonable defaults. Opt-out for encryption might sound right but if I lose my data because I lost the password, whome will I blame? It's never my fault! (And there is no key service...)

I'm glad I don't have to decide such things. :P

---

### Post by gnomeuser on 2008-12-25
> **vade said:**
> How does file system en/decryption affect performance? Is the difference to non-encrypted noticeable?

Funny you should mention it, recent investigation into this very question was just made on the Fedora mailing list. For regular use, the impact is not a problem.

It's the same thing with filesystem compression really, IO is so slow and CPUs are so fast that it really doesn't make a big difference (in fact compression might even make things faster by making IO less but that is a different story all together).

For reference, the long encryption thread can be found here:
[https://www.redhat.com/archives/fedora-devel-list/2008-December/msg02516.html](https://www.redhat.com/archives/fedora-devel-list/2008-December/msg02516.html)

---

### Post by MacUntu on 2008-12-25
Phoronix did some benches with 9.04 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_jaunty_encrypt&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_jaunty_encrypt&num=1) but tbh. I don't know what to think about it.

---

### Post by ronacc on 2008-12-25
@ gnomeuser your solution would be acceptable although I would prefer opt in , I would choose not to encrypt for my own reasons . I have other security measures that I feel are adequate and if someone unauthorised gains physical access to my machine I have far greater problems than them stealing some files and data that are publicly available anyway . More systems by far are compromised by ill thought out actions of the user than by direct attack from the outside .

---

### Post by gnomeuser on 2008-12-25
> **ronacc said:**
> @ gnomeuser your solution would be acceptable although I would prefer opt in , I would choose not to encrypt for my own reasons . I have other security measures that I feel are adequate and if someone unauthorised gains physical access to my machine I have far greater problems than them stealing some files and data that are publicly available anyway . More systems by far are compromised by ill thought out actions of the user than by direct attack from the outside .

I'm not saying full disk encryption is definitely always the right solution. There are practical problems to consider but I believe that we should design solution that are secure without getting in the users way. This is one reason I have pushed since the first release of Ubuntu to have SELinux deployed by default.

But let's example one problem, currently the only way to unlock the partition is using a password. One password. This means on a family machine you would have to have everyone remembering it (and mine in +20 randomized characters.. yes I remember that, not written down anywhere). This might not be optimal, now if we could unlock it with fingerprints e.g. everyone in the family could be scanned in and that would solve that problem or a solution could be investigated where every family member had his/her home folder encrypted (and unlocked as part of the login) but the base system would not be, to allow booting. It's all in finding the solution where security does it's job quietly in the background.

The solution should not be to disable it in every case, it would be to fix it. Look at SELinux it started as a very restrictive system which functioned basically as a white list. This exposed a lot of problems but in the policy and the applications which were contained. Now after years of development and refining we are at a point where SELinux quietly does it job in the background, in any normal scenerio the user never even knows it's there. Yet SELinux is very helpful in preventing and containing attacks. 

I believe we can make encryption serve the user in the same way. Finding the correct solution though is not being helped by not working on the problem and disabling by default.

---

### Post by vade on 2008-12-25
> **MacUntu said:**
> Phoronix did some benches with 9.04 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_jaunty_encrypt&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_jaunty_encrypt&num=1) but tbh. I don't know what to think of it.
I saw only one thing to worry about: [huge write performance hit](http://www.phoronix.com/scan.php?page=article&item=ubuntu_jaunty_encrypt&num=4). 35MB/s unencrypted versus 14MB/s encrypted. There's a good reason to not enable eCryptfs encryption by default. (Or at least tell the user that safety means a slower computer.) And this was with a very powerful quad core cpu!

---

