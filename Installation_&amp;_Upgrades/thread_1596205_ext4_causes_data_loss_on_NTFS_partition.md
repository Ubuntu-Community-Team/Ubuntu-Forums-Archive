---
title: "ext4 causes data loss on NTFS partition???"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by GMHilltop on 2010-10-14
Is this possible with a hard shut down?

I had everything backed up and imaged, so recovery was very easy . . . here is what happened:

sda1 was an NTFS partition with windows 7 installed.
sda2 was another NTFS partition with another version of windows 7 installed.
sda3 ===> I then installed 10.04.1 LTS here and formatted with ext4
(there were 2 other partitions for data storage and a 1GB swap file at the end of the disk.

I did the Ubuntu updates next with no problems.

(Now I still don't have a lot of experience with Linux, but, there then came a recommend "Hardware Drivers" update notice balloon)

It was an nVidia graphics driver   **[Recommended]**  So I thought to myself, "Sure, lets give it a try, it's [Recommended] after all. "

.... yeah that didn't turn out so well.

Not only would Ubuntu not boot, I had to do a hard shutdown by holding the power button down after the restart attempt.

Now for the weird part:

I couldn't boot either Windows 7 partition, and it didn't matter whether I used Grub2 **OR a supergrub disk**.  (The super grub disk I had used flawlessly up to this point) There was something that disappeared on the Windows installation (I don't remember exactly what the error code was).

SO, to test my theory, I just imaged ONE of the Windows 7 OS's back to its partition using Acronis - and nothing else was touched.

When presented with the Grub2 boot menu, I selected it, and _**it booted perfectly.**_

The Ubuntu OS was still screwed, and the OTHER NTFS partition still wouldn't boot until I imaged it back also.

I would not have thought that working with that ext4 partition, and having a failure there would cause data loss on OTHER partitions (It doesn't make sense).

After doing some searching, I have come across posts that 'suggest' that this has happened in the past with power failures.

I've read about data loss with ext4 regarding renaming and changing files and then having THAT data get screwed up.  I am not totally sure that that is fixed, but it is NOT what I am asking about here.

My question:

Is anyone familiar with ext4 file systems, and a bad install/upgrade/power loss/hard shutdown/etc,etc causing data loss on OTHER partitions?

That sure seems to me to be what happened here to me.

NOTE:
*Equipment was a Sager NP5125 (originally designed with dual video cards and to be used with "Optimus technology - that might be why the [Recommended] driver didn't work, but doesn't explain the data loss on the other partitions) *

---

### Post by Mark Phelps on 2010-10-14
You sure you had two different Win7 installs? Or was the more typical situation where the first NTFS partition has the Win7 boot loader files, and the second has the Win7 OS files.

Asking because GRUB sees them BOTH as Win7 -- leading to confusion when folks try to boot from the second partition -- which will NOT boot because it does not have the boot loader files.

---

### Post by endotherm on 2010-10-14
the power failure would not have caused ext4 systems to mess with ntfs partitions, but much more likely affected your disk controller, which of course can mess with the data in any partition, or just prevent you from accessing the data even though it is still there and integral. 
have you tried any HDD diagnostics, and have you run fsck/chkdsk from a boot disk for both types of partitions? also check the SMART data to see if it thinks your drive is still fit.

---

### Post by GMHilltop on 2010-10-15
> **Mark Phelps said:**
> You sure you had two different Win7 installs?

I do this a lot.  I am 100% sure.

 > **Mark Phelps said:**
> Or was the more typical situation where the first NTFS partition has the Win7 boot loader files, and the second has the Win7 OS files.

I imaged the OS to both partitions, and then changed the UUID of the 2nd Partiton so that Grub2 wouldn't get confused, and could Identify them via their unique UUID.  I then booted them both using a super grub disk to make sure they worked.
Prior to installing Ubuntu with the ext4 extension I had installed it with the ext3 extension, and everything booted fine (both sda1, sda2, and sda3).

> **Mark Phelps said:**
> Asking because GRUB sees them BOTH as Win7 -- leading to confusion when folks try to boot from the second partition -- which will NOT boot because it does not have the boot loader files.

My experience has been that the confusion arises If you have 2 partitions with the SAME UUID (as would be the case if I put the same image on 2 different partitions and DID NOT change one of the uuid's)

Thanks for the response though - It was definitely something else.

---

### Post by GMHilltop on 2010-10-15
> **endotherm said:**
> the power failure would not have caused ext4 systems to mess with ntfs partitions, but much more likely affected your disk controller, which of course can mess with the data in any partition, or just prevent you from accessing the data even though it is still there and integral. 

There was no power failure.  I was trying to install a *recommened *graphics driver.
[INDENT]> It was an nVidia graphics driver   **[Recommended]**  So I thought to myself, "Sure, lets give it a try, it's [Recommended] after all. "

.... yeah that didn't turn out so well.

Not only would Ubuntu not boot, _**I had to do a hard shutdown**_ by holding the power button down after the restart attempt.[/INDENT].... unless the hard shutdown can affect the disk controller as you had mentioned -- I don''t know what I am talking about here, but I would be surprised that that would mess with data in any partition, but like I said I don't really know much about disk controllers.

> **endotherm said:**
>  . . . have you tried any HDD diagnostics, and have you run fsck/chkdsk from a boot disk for both types of partitions? also check the SMART data to see if it thinks your drive is still fit.

No I didn't.  Mostly because I don't know what those are ( fsck/chkdsk  - I am still learning here ), and because I just re-imaged the the partitions with EXACTLY the same images that were on them before.  Reloaded Ubuntu and everything worked perfectly.

I am familiar with SMART, but I don't know how to check the data.

I did try to reproduce the same problem (updating to the [Recommended] driver) and had the same lockup of ubuntu ( I still think that it might be related to this being a very new computer - but I can't say for sure) only this time I could still boot the sda1 and sda2 partitions with supergrub, where as before I couldn't.

Seems very strange to me.

---

### Post by GMHilltop on 2010-10-15
> **moneer said:**
> I have the same problem when the first time I install ubuntu.. lack of knowledge cause my data loss..
But lucky I get help from [online data recovery]("http://i-data-recovery.com") expert to recover my data in windows partition. check this: http:i-data-recovery.com . maybe he can help with your data. 

Regards,
Moneer

Thanks, but I didn't loose anything - I had the images, and they were just clean installs.  I am just testing Ubuntu 10.04.1 as it sounds like a lot of people have has stability issues.  But it sounds like there are some issues with ext4 still.

Could it be a combination of the 2 somehow???

I am not sure.

But I should check the drive as endotherm mentioned.  I just have to learn what those commands do and how to check the smart data.

---

### Post by CharlesA on 2010-10-15
Hi.

Have you tried booting off a Win7 disk and selecting "startup repair" then seeing if Win7 will boot?

It sounds like grub messed something up.

---

### Post by coffeecat on 2010-10-15
Long shot here, but did you have the two NTFS partitions mounted in Ubuntu when you did the hard shutdown? If they were unmounted abruptly like that, that could conceivably have led to filesystem corruption.

Just for future reference, if you're ever faced with a locked solid Linux system again (doesn't happen often I assure you :|), then the magic key combination will allow you to shutdown gracefully. More here:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

---

### Post by li-nux or lie-nucks? on 2010-10-15
I have had a very similar experience which I have posted on the forum elsewhere. PC setup pretty much the same except one internal drive for Windows OS and another internal drive for User folders (my documents etc.).
Now for the weird part (which I don't have an answer on yet). Boot from the live CD and one of the internal disks begins thrashing. Reboot to find out what's going on and find a partition on one or both disks are lost. I have replicated this issue four times now and each time is the same result. Luckily everything is backed up so just restore. When I have been able to get into Windows I can see in the disk management tool that the affected drive has been altered to RAW format.
Cant see why this would happen just booting live from the CD without even beginning the install. 
:confused:

---

### Post by GMHilltop on 2010-10-16
> **CharlesA said:**
> Hi.

Have you tried booting off a Win7 disk and selecting "startup repair" then seeing if Win7 will boot?

It sounds like grub messed something up.

No I have not - I just re-imaged the partitions and everything was fine.  There definitely was something to do with the "Hard Shutdown" that messed those other partitions up.

[INDENT]I'll digress a moment from the subject of this thread.
NOTE TO ALL:  I found multiple instances where other people had tried the Ubuntu 10.04 [recommended] drivers on the NP5125 Notebook and rebooted to a "Black" screen.

[http://forum.notebookreview.com/sager-clevo-reviews-owners-lounges/499301-official-sager-np5125-owners-lounge-162.html#post6777118](http://forum.notebookreview.com/sager-clevo-reviews-owners-lounges/499301-official-sager-np5125-owners-lounge-162.html#post6777118)

[http://forum.notebookreview.com/sager-clevo-reviews-owners-lounges/499301-official-sager-np5125-owners-lounge-62.html#post6600724](http://forum.notebookreview.com/sager-clevo-reviews-owners-lounges/499301-official-sager-np5125-owners-lounge-62.html#post6600724)

[http://forum.notebookreview.com/sager-clevo-reviews-owners-lounges/499301-official-sager-np5125-owners-lounge-106.html#post6683931](http://forum.notebookreview.com/sager-clevo-reviews-owners-lounges/499301-official-sager-np5125-owners-lounge-106.html#post6683931)

etc, etc, etc.

I haven't tried this but this might be a solution for those who are looking:

[http://ubuntuforums.org/showthread.php?t=1571031](http://ubuntuforums.org/showthread.php?t=1571031)

[/INDENT]In response to the quote above - Why would Grub2 have anything to do with "Messing" with the other partitions?  I am not an expert, but it doesn't seem to me like that would have done it - no?

---

### Post by GMHilltop on 2010-10-16
> **coffeecat said:**
> Long shot here, but did you have the two NTFS partitions mounted in Ubuntu when you did the hard shutdown?

No, I don't think so.  I installed the [Recommended] drivers and then "Restarted" the computer.  So I think they would have been 'unmounted'.

Grub menu came up, I selected Ubuntu, and it froze with a black screen.


> **coffeecat said:**
>  . . . Just for future reference, if you're ever faced with a locked solid Linux system again (doesn't happen often I assure you :|), then the magic key combination will allow you to shutdown gracefully. More here:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)


Cool LINK!
Thanks for that!  I always wondered what the heck 'Sys Rq' was all about.

> **coffeecat said:**
>  . . . Just for future reference, if you're  ever faced with a locked solid Linux system again (doesn't happen often I  assure you :neutral:) . . . .

I hope you are right, but there is a LONG thread in which it sounds like there are A LOT of people having trouble with the 10.04 version causing freezes and lock ups.

It is up to something like 117 pages now:
[URL="http://ubuntuforums.org/showthread.php?t=1478787"]
http://ubuntuforums.org/showthread.php?t=1478787[/URL]

Any idea what's up there?

---

### Post by GMHilltop on 2010-10-16
> **li-nux or lie-nucks? said:**
> I have had a very similar experience which I have posted on the forum elsewhere. PC setup pretty much the same except one internal drive for Windows OS and another internal drive for User folders (my documents etc.).


What Kind of machine was it?  Was it using optimus technology (integrated and dedicated video cards)?

Where you using ext4 as the file extension on the Linux installation?


> **li-nux or lie-nucks? said:**
> Now for the weird part (which I don't have an answer on yet). Boot from the live CD and one of the internal disks begins thrashing. Reboot to find out what's going on and find a partition on one or both disks are lost. I have replicated this issue four times now and each time is the same result. Luckily everything is backed up so just restore. When I have been able to get into Windows I can see in the disk management tool that the affected drive has been altered to RAW format.
Cant see why this would happen just booting live from the CD without even beginning the install. 
:confused:

Could the thrashing be that it is 'looking' for the partitions that somehow had the data messed up?  (I have no clue) 

From what I am hearing, it sounds like a 'hard shutdown' IS NOT a good thing when running Linux.

I may not have that exactly right, but it sort sounds like that -- unless it has something to do with the original question posted when I started this thread ---- that being, does it have something to do with it being an ext4 extension?

---

### Post by SeijiSensei on 2010-10-16
What does 'sudo fdisk /dev/sda' say are the partition types?  Is sda3 marked as Linux? sda1 and sda2 marked as HPFS/NTFS?

---

### Post by GMHilltop on 2010-10-16
re:
> **coffeecat said:**
>  ...
[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

coffeecat, which would you recommend to shut down a frozen system?
 Alt + SysRq + o

or would you start with something like:
Alt + SysRq + f

remember we can's "see" anything on the screen.

---

### Post by GMHilltop on 2010-10-16
> **SeijiSensei said:**
> What does 'sudo fdisk /dev/sda' say are the partition types?  Is sda3 marked as Linux? sda1 and sda2 marked as HPFS/NTFS?


They are NTFS partition types ===> sda1, and sda2

sda3 where i installed linux was ext4 when this happened.

Because of the number of data loss issues that were 'implied' with regards to ext4, I thought that it might have something to do with it.

... now there appears to be an issue with the [Recommended] drivers that contributed to 'triggering' this incident for me (the black screen and freeze up are reproducible) but the only data loss I had was with the ext4 file system being in place.

I still get the freeze up with the ext3 - but not data loss (even with a hard shutdown).  I just have to reload Ubuntu.

Now, I didn't try the freeze up with ext4 in place again, because I didn't have time to play with it any more but it sounds like **li-nux or lie-nucks**  did reproduce the data loss -- I just don't know what his file system was.

---

### Post by coffeecat on 2010-10-16
> **GMHilltop said:**
> I hope you are right, but there is a LONG thread in which it sounds like there are A LOT of people having trouble with the 10.04 version causing freezes and lock ups.

It is up to something like 117 pages now:
[URL="http://ubuntuforums.org/showthread.php?t=1478787"]
http://ubuntuforums.org/showthread.php?t=1478787[/URL]

Any idea what's up there?

I don't doubt that there are issues with some combinations of hardware and particular versions of Ubuntu. Complaints of freeze-ups have been made with every version of Ubuntu. Perhaps Lucid is worse in this respect, perhaps better; I don't know. However, I would put serious money on this affecting a very small minority of hardware combinations. With regard to long threads like that, experience has taught me to avoid them. They tend to have a bandwagon effect with irrelevant posts. And I'd bet even more serious money that with a thread about freeze-ups a significant proportions of the posters that have jumped on the bandwagon have hardware problems such as bad RAM, failing PSUs - that sort of thing.

> **GMHilltop said:**
> 

coffeecat, which would you recommend to shut down a frozen system?
 Alt + SysRq + o

or would you start with something like:
Alt + SysRq + f

remember we can's "see" anything on the screen.

It's all in the link. You don't have to see anything on screen - just press the keys. Alt+SysRq+ R-E-I-S-U-B is recommended for the reasons given. What I forgot to mention is that on some machines you have to use the AltGr key on the right of the space bar.

---

### Post by kyllikki on 2010-10-24
I was suffering data loss running a dual boot system (NTFS/EXT4), perhaps nodelalloc needs still be added to fstab to prevent problems as described in this article...  [http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/]("http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/")

---

