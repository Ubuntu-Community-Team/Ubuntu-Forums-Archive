---
title: "Question on adding new drive"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by rillip on 2007-03-28
I'm currently dual booting  Win 2k and Kubuntu 6.06 on my 40 gig PATA hard drive.  hda-1 is my 19g linux, hda 2 is swap, something like 1 gig, and hda 3 is my Windows partition at around 20 gig.  Thsoe numbers aren't exact but you get the idea.

I've got a new 80 gig sata drive, but want to keep the old pata as well.  So, here's my dilema:

What is the easiest way to maintain my dual boot system with this new drive?

What I would like to have happen is to put one OS on the new drive, one on the old drive, and still have Grub choose the OS. I can accept having one on each and chosing the OS by boot priority if neccessary, but this is less than ideal.

I think I can resize the partition using the LiveCD parition resize util, but I'm not sure how to keep grub working unless I leave Linux on the 40 Gig PATA, which is not what I want to do.

I've also considered using the PATA as just an archival drive, i.e. split the SATA to a dual boot, then use the LiveCD to get rid of the swap parition, and just put my items I'm not really using right now on the PATA, so that I get the best performance on both OS's.

Have any of you done something like this before?  Am I completely overthinking this?

---

### Post by kidders on 2007-03-28
Hi there,

> **rillip said:**
> What I would like to have happen is to put one OS on the new drive, one on the old drive, and still have Grub choose the OS.That seems like a strange way to organise your data, considering that the result would be that you would only ever be using one hard disk at a time. Imo it would be more sensible (in performance terms) to use both disks as much as possible, *all* the time.

I would suggest something like this...
[LIST]
[*]Putting the Linux and Windoze systems on separate disks.
[*]Putting Linux's swap on Windoze's disk, and Windoze's pagefile on Linux's.
[*]Perhaps you could put your personal files on both disks at the same time (using software RAID mirroring), so you wouldn't lose important data, even if one hard disk blew up.
[/LIST]

Alternatively, you could spread bits of both OSs all over the place. For instance, all your applications (for both OSs) on one disk, and all your system/personal files on another. Particularly since your hard disks are on different buses, you should get a good degree of parallel I/O happening, which can boost performance. For example, both Linux & Windoze will greatly appreciate _not_ having their virtual memory on the same drives as their system files.

> **rillip said:**
> I'm not sure how to keep grub working unless I leave Linux on the 40 Gig PATA, which is not what I want to do.Your bootloader is a minor enough issue, really. You can install Grub at your leisure onto either hard disk. There are a few things to watch out for though...

[LIST]
[*]If you install Grub onto your new hard drive, you'll wind up with two bootloaders, only one of which you'll really want to use. Your system will pick the one that comes first in the BIOS boot order. To avoid getting confused about which is which, you should do something like adding slightly different menu options to each one, so you can recognise them.
[*]When you have more than one hard disk, modern BIOSes make it easy to get confused about setting Grub up in the first place. It's important to remember that the disk that comes first in your boot order is not necessarily the disk that Grub will call "hd0".
[*]If you've never played with bootloaders before, always assume you're going to fail terribly. (Pessimistic, amn't I?!) Have a bootable CD to hand, and practice a procedure called "chrooting", so you can operate your Ubuntu install without actually booting from it.
[/LIST]
People often find bootloaders confusing. If I were you, I'd deliberately install one on *both* hard drives, and make sure they both work properly. That way (at least for Linux) your disk orders won't matter, and you only have to worry about keeping MS happy. It would be nice if you felt free to mess around with your cables (or your BIOS), without having to worry about whether your PC will even boot up, when you put everything back together again.

> **rillip said:**
> I've also considered using the PATA as just an archival drive, i.e. split the SATA to a dual boot, then use the LiveCD to get rid of the swap parition, and just put my items I'm not really using right now on the PATA, so that I get the best performance on both OS's.Careful... removing your swap will *kill* Linux's performance.

> **rillip said:**
> Am I completely overthinking this?No, not at all. :-) You have an opportunity now to set things up just the way you want them. You might as well use it hehe.

---

### Post by rillip on 2007-03-28
> **kidders said:**
> Hi there,

That seems like a strange way to organise your data, considering that the result would be that you would only ever be using one hard disk at a time. Imo it would be more sensible (in performance terms) to use both disks as much as possible, *all* the time.

I would suggest something like this...
[LIST]
[*]Putting the Linux and Windoze systems on separate disks.



But isn't that what I first started out suggesting?  One on the new disk, the other on the old...?

> **kidders said:**
> 
[*]Putting Linux's swap on Windoze's disk, and Windoze's pagefile on Linux's.
[*]Perhaps you could put your personal files on both disks at the same time (using software RAID mirroring), so you wouldn't lose important data, even if one hard disk blew up.
[/LIST]


One drive is PATA, one is SATA, my understanding is that a) you can't do that b) even if you could, it'd drag the performance way off the SATA, as it would only work as fast as the slowest drive and b) if you do raid 1 (mirroring) that your drive will only be as big as the smallest drive, which makes getting the new, bigger, better drive useless.  Either my assumptions here are all wrong or I'm misunderstanding horribly.

> **kidders said:**
> 
Alternatively, you could spread bits of both OSs all over the place. For instance, all your applications (for both OSs) on one disk, and all your system/personal files on another. Particularly since your hard disks are on different buses, you should get a good degree of parallel I/O happening, which can boost performance. For example, both Linux & Windoze will greatly appreciate _not_ having their virtual memory on the same drives as their system files.


While I'm reluctant to putting anything on the slow PATA, I have it and need the space.  I can understand how the parallel IO will help signifigantly.  I'm thinking that the swap is probably used less than the system files, meaning I'd want the swap on the smaller, slower, PATA.  My thinkig is you only swap when there's not room in main memory, but any time you load anything, save anything, open a file, etc. you have to read from disk, so that's where you want the performance.  Opinions?

> **kidders said:**
> 
Your bootloader is a minor enough issue, really. You can install Grub at your leisure onto either hard disk. There are a few things to watch out for though...

[LIST]
[*]If you install Grub onto your new hard drive, you'll wind up with two bootloaders, only one of which you'll really want to use. Your system will pick the one that comes first in the BIOS boot order. To avoid getting confused about which is which, you should do something like adding slightly different menu options to each one, so you can recognise them.
[*]When you have more than one hard disk, modern BIOSes make it easy to get confused about setting Grub up in the first place. It's important to remember that the disk that comes first in your boot order is not necessarily the disk that Grub will call "hd0".
[*]If you've never played with bootloaders before, always assume you're going to fail terribly. (Pessimistic, amn't I?!) Have a bootable CD to hand, and practice a procedure called "chrooting", so you can operate your Ubuntu install without actually booting from it.
[/LIST]
People often find bootloaders confusing. If I were you, I'd deliberately install one on *both* hard drives, and make sure they both work properly. That way (at least for Linux) your disk orders won't matter, and you only have to worry about keeping MS happy. It would be nice if you felt free to mess around with your cables (or your BIOS), without having to worry about whether your PC will even boot up, when you put everything back together again.


So I'm understanding that Grub can work across disks, as long as it's on the disk that is booted first? I'm also sensing that Grub may automatically change the configuration menu to reflect his, but that it may get pretty confusing.?

> **kidders said:**
> 
Careful... removing your swap will *kill* Linux's performance.



What I meant was that I would leave the paritions intact for data storage, but both OS are on the SATA (including the swap; I wouldn't just deep-six it forever).

So, do I put an OS on each disk, or do I split both disks and put OS on one, swap on the other?  If so, do I want the data on the same drive as swap, the system, or both?  Will it matter?

I'd like to get the best performance I can out of this, which would really be a major upgrade to buy decent drives and RAID 'em, but given the hardware I have, how can I best boost performance and still have more space? (More space was the impetus for the drive, since I ran linux so low it couldn't create the files neccessary to startx and I had to work out of the command prompt for a week and a half while I figured it out...)

---

### Post by kidders on 2007-03-28
Hey again,

> **rillip said:**
> One drive is PATA, one is SATA, my understanding is that a) you can't do that b) even if you could, it'd drag the performance way off the SATANeither is true, thankfully. Additionally, if you were to use RAID like this, you'd probably only be interested in devoting part of each drive to the array, so disk size differences would probably be irrelevant.

Also, don't forget that doubling the number of hard disks in your PC doubles the data loss probability, so even if there *were* a performance penalty to worry about, some users would still think RAID worthy of consideration. If you don't like the sound of my suggestion, that's okay though. :-)

> **rillip said:**
> While I'm reluctant to putting anything on the slow PATA, I have it and need the space.If you were interested in putting numbers to your system performance under various circumstances, you could try comparing the real speeds of your hard disks. It might be interesting to see which is slower, and by how much:

[LIST]
[*]Two processes performing large sequential reads from two partitions on your fast drive. (ie emulating heavy simultaneous swap & userspace usage.)
[*]Two processes doing the same thing with one partition on each drive. (ie measuring the difference keeping swap away from "real" data would make.)
[/LIST]


> **rillip said:**
> I can understand how the parallel IO will help signifigantly.  I'm thinking that the swap is probably used less than the system files, meaning I'd want the swap on the smaller, slower, PATA.Another variation would be to put swap on both disks. On server configurations for instance (which probably isn't what you're doing), I often allocate rather a lot of swap on different devices, but I prioritise it so the system actually uses it in a particular order. Your reasoning seems sensible to me though, in that swap I/O is going to be 100s of times slower than RAM I/O anyway, so I can't imagine using up your fast disk (so you can have swap that goes 320 times slower than RAM, rather than 345 times slower) would be worth it.

> **rillip said:**
> So I'm understanding that Grub can work across disksI'm not quite sure what you mean by that. Grub can't spread itself over multiple disks, but it *can* (obviously) boot operating systems that aren't on the same disk it is, and you *can* install it on several disks at the same time.

It looks like I phrased parts of my last post badly ... sorry about that. Let me try again hehe.

Imagine you've just done a system update, your PC stops booting, and you want to figure out why. If you have two hard disks, things can get confusing, particularly if they're on different I/O buses like yours are. Typical problems (often encountered by posters here) are:

[LIST]
[*]At some point in the past, Ubuntu installed Grub on the wrong HD, but you didn't notice because both configurations were compatible with eachother. Now they're not, but you don't realise that you've been using an out-of-date bootloader for the past two months.
[*]To keep Windows happy, you change your hard disk boot priority, causing Ubuntu to number your devices differently *or* causing Grub to do so, but not both. Your system sort of boots, but dies half way through.
[*]Sometimes, users don't spot the distinction between their physically "first" disk drive and the one that's first in their boot order. (Many BIOS configurators make the difference sort of wooly.) Then, when they try to manually reconfigure things, their system starts to throw paradoxical error messages at them.
[/LIST]

There's an endless list of them! Essentially, if you can sort out exactly how bootloaders work in your head, you can almost always fix booting problems in 3 minutes flat, because what's gone pear-shaped is just sorta "obvious" to you. It's pretty important to be able to do it, because Windows and Linux enjoy screwing with eachothers' boot processes, so it's _gonna_ happen to you! 


Anyhow, how to be sure you're squeezing the very best performance out of your PC is not an easy question to answer, unfortunately. Your typical usage patterns and the I/O caching & throughput specs of your motherboard are two major factors. There are other issues, of course, such as filesystem type & block size decisions you may make later.

Trying to decide which combinations of changes would have the biggest impact is non-trivial. :-( You may find, for instance (and this is just an example), that reading movies off your fast hard disk with standard 1K Ext3 blocks could be slower than reading them off your slow hard disk with 4K ReiserFS blocks. Equally, you could discover that your read-ahead caching is so good that putting swap and your Linux system on different devices actually makes no difference.

I'm very conscious that all that rambling I've just done isn't very ... well ... definitive. In my last post, I was hoping to draw your attention to the idea that there are lots of ways of organising things, but you seem experienced enough to know that already. :-)

---

### Post by rillip on 2007-03-29
I talked with one of the guys tonight about how to do setup the paging on Windows.  What I think I'll start with is formating the SATA with three partitions, one for Linux (whatever the default format, is, I'm not going to give myself the headache of trying to figure out what format/block size/etc to use), one Fat (16 or 32?  I recall reading that Linux can read Fat, which will help me pull over my data, I'll research which one) and one NTFS.  I'll just leave the OS and swap/paging the way they are and put my data on the SATA.

After a little bit of trivial testing, I'll try moving my swap to the faster drive/paging to the faster drive with the data (data is pretty well going to have to go on the larger drive, in general).

I think I'll stick with one of those two configurations.  Having the parallel IO is too appealing to bog one of them down, and having the swap/paging divided just seems like too much trouble if it breaks.  And I'm not interested in messing with reinstalling and a potential fight with Grub, so I'm going to leave the OS's where they are.

Setting up a raid device with this scenario just complicates things way too much, a) because I have limited experience with raid and b) because I'll end up with partitions that are part PATA, part SATA, and it'll be too difficult for me to do any sort of meaningful analysis of results. And frankly, data perisistance isn't enough of a concern to warrant doing a mirror array, I could honestly backup most of my important documents on a single floppy if I really wanted to, and even those I could recreate without much issue.

Thanks a lot for the discussion Kidders, you've helped a lot.  I'll post my rather crude results some time this weekend after I've had a chance to play around with it.

On a side note, is it just me, or does Linux (or at least Kubuntu 6.06) play very badly with nearly full drives?  I went to uninstall a program to free up disk space and it told me it couldn't because the disk was full... :?  And Opera seems to just disappear randomly if my disk gets full.  And if Ireboot, I'm sure I'll run into xserver not being able to get the gui running.  The reason I figured it out last time was because I tried to run a man on a command I was unfamiliar with that had been suggested as a fix, and got a IO error, not enough space on running man.  Annoying to say the least, but I felt proud to figure it out, even though it was my own fault! :) :p

---

### Post by kidders on 2007-03-29
> **rillip said:**
> On a side note, is it just me, or does Linux (or at least Kubuntu 6.06) play very badly with nearly full drives?Yes. Linux reacts **_very_** badly to having nowhere to write stuff. The operating system is fundamentally filesystem-based (a bit like MacOS is), and will behave unpredictably unless there are at least a few hundred kilobytes of space available to it at all times.

By the way, I'm glad there was *something* useful buried in my ramblings!

---

### Post by rillip on 2007-04-01
Okay, I think I have it almost done.

After quite a while of duking it out with my bios, Windows drivers and a raid setup, the new sata hdd is partitioned and visible in both OS's.  I have the following setup.  I made these partitions using the Eddgy installer.

(80 gig total) ~ 37 gigs ex3, 29 gigs ntfs, 3 gig swap, 8 gig fat 32.

Fat 32 and NTFS were already formated in Windows.  Was able to enable the fat32 after moutning to /mnt/share without issue.

I never could figure out how to format the other partitions from the disk and partition manager thing, so I just Googled the commands and did it from the terminal.  Was able to enable the ex3 without issue.

At the same time as I got the command for formating, I found the mkswap command. Ran that on the 3 gig swap partition, no issues. Enabled it as well, no issues.

Now here's my beef - I'd like to disable the miniature space I had alotted before (700 megs) on the PATA and reassign it, but I don't want to destroy my system either.  Is it safe to disable the PATA swap now that the SATA swap is active, then delete the partition and resize?

---

### Post by kidders on 2007-04-01
This all sounds good. :-)

> **rillip said:**
> At the same time as I got the command for formating, I found the mkswap command. Ran that on the 3 gig swap partitionWoo that's big. Are you sure you need all that?

> **rillip said:**
> Is it safe to disable the PATA swap now that the SATA swap is active, then delete the partition and resize?I guess so, although I would always avoid resizing partitions where possible. You could always just use the 700M as a /var or something.

---

### Post by rillip on 2007-04-01
> **kidders said:**
> This all sounds good. :-)


I make this sound good?   Actually, the whole thing was a total ordeal that was extremely stupid.  First, it's a  SATA 1 (i.e. 150) drive  as that's all my mobo will handle.  I know SATA II (i.e. 300) is supposed to be backward compatible, but frankly I've read that alot of manufacturers (esp. cheap models) fake the SATA with software/firmware and I just didn't feel like going to the hassle of getting a 3, nerfing it, having the backward compatibility not be what it should, etc.  I had to search for about six hours when I couldn't detect it as to what was wrong.  Even though it's a SATA 1, there's A FREAKING JUMPER(!!!!!) to set it to use 150 mode.  What other mode is there, it's SATA 1!!  Sheesh.  And of course it's not a standard jumper size, it's one you have to have an electron microscope to see.

So after finding that, I got my wife's working.  I was planning on showing a friend today how to do all this and so hadn't done mine yet.  I go to do mine, set the jumper, still not detected. I go to Windows, see no sata controller, and try to install one from my mobo CD.  It tells me no, no compatible hardware.  About  an hour later, I think to check the BIOS and OnChip SATA is disabled (:oops:)  After that, I get the partitions all set up, I'm home free, right?

Well, not so much.  I try to use them, and the partitions have been created/formated/otherwise set up as owned by root.  How useful, since I don't have a root user set up.  I'll just go to the command line and sudo every file move... forget the gui, I just installed that on a whim anyway... :roll: So I go to the commandline, chown it (unsuccessfully because I've never used chown, and have to man chown to get the arguments in the right order).  But now, it IS all good and working  \\:D/ And I'm proud of myself as I've done it all on my own, pretty much.

> **kidders said:**
> Woo that's big. Are you sure you need all that? 

Heck no, I'll never use all that.  I was going to make it 2, which was pretty reasonable, but 3.1...x was what was left over when I started splitting up my drives, so I just went for it.  I've had this computer for about 6 years already, so it's entirely likely I could have it when the next gen of apps comes out and needs that sort of RAM (i.e. gamezz!!!  If I can get them to run okay in wine :| )  Who knows when you could need massive ammounts of swap space?   I might pair it down a tad.


> **kidders said:**
> 
I guess so, although I would always avoid resizing partitions where possible. You could always just use the 700M as a /var or something.

I'm a resizing fool!  No really I am. :D  I haven't had any problems yet, and I don't see any reason not to fiddle with it until it breaks, that's kind of the point of setting up this system.  But I didn't want to break it 1000000% by deleting a swap partition that was in use and dealing with the ensuing havoc.

Thanks for the quick update, now it's time to go gank that swap partition.. :twisted:

Edit:  Good thing I didn't get around to that last night.  I booted this morning and found no drives(!!??). Looked and what do you know, I hadn't chosen to enable them on start up... :oops:

---

### Post by kidders on 2007-04-01
> **rillip said:**
> Actually, the whole thing was a total ordeal ... And of course it's not a standard jumper size, it's one you have to have an electron microscope to see.Yikes! You've been busy! As you've noticed, you *do* need to tread carefully in the SATA world ... many controllers are buggy, fake, incomplete, or otherwise strange. (As if life isn't complicated enough.)

Anyhow, now that you know how file ownership works, be sure to check your work for security holes. Linux is merciless ... if something's permissions are too liberal, or its ownership is not quite right, the OS will make absolutely no effort to protect you from malicious software/people.

Swap-wise, allocating too much of it will only tempt you to ask your computer to do things it wasn't designed for. In general, the amount of swap you have on a desktop PC shouldn't get too close to the amount of RAM you have, unless you want to be able to hibernate. Don't forget that I/O to swap is hundreds of times slower than I/O to RAM (and has the knock-on effect of using up time that *should* be spent accessing your files), so one's not really a substitute for the other!

Everything possible seems to have gone pear-shaped for you. :-( Just think how easy doing this is gonna be for you the next time though. Hehe.

---

### Post by rillip on 2007-04-01
Yeah, it should all be a cake walk next time!

I work for a hosting company and we typically leave everything at 644 or 755. I have it on 644 since I chowned to me. Any potential issues with this?  As I'm running all my programs as myself, is there any issue with 600?

---

### Post by kidders on 2007-04-01
Not usually. I was just checking... you'd be surprised how many people decide Linux is just being awkward, and say "Oh drat... chmod -R 777 *".

---

### Post by rillip on 2007-04-02
Yup, cmod 600 works fine, take that you dirty hackers! :p

---

