---
title: "[SOLVED] CD md5sum doesn't match, but passes integrity check"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by keyboardashtray on 2007-07-06
Hello - 
The md5sum of my Live CD of Ubuntu 7.04 does not match the hash at the site. The md5sum of the original ISO that I downloaded (before burning) does match perfectly, and when I do boot from the Live CD and run the integrity check, it finds no errors. I am also able to run the Live CD and play around in Ubuntu, and everything seems fine (except Rythmbox locked up a couple times on the net radio, and overall seems to struggle with the net radio, but I just chalked that up as a speed issue from running it from a CD).

The [documentation]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29#head-0e24f0b47485dda966483fe6b4afb79c6531114c") seems a little hazy on the issue of the CD's md5sum, both on how to check it and how much it matters ("However, .iso files can easily be tampered with in such a way that this method shows no errors"). I'm running windows, so I had used the link to the graphic md5sum checking utility in the windows section. The method Ubuntu's documentation describes for checking the CD talks about typing commands and didn't seem to apply to the Windows method, I just Explored the CD and found an md5sum file on the CD, and used Send To to send it to the checking application.

I don't know if this matters, but the md5sums of the 2 CDs I have burned so far match each other perfectly (ee3b353e0566d7969e9887f54090eb07). My last burn I went as slow as my utility would allow (4x). If there was an error in burning, wouldn't it be more random - why would two CDs match? 

If the original pre-burned ISO's md5sum matches but the CD doesn't, but the CD passes the integrity check, is it safe to use?

Thank you.

---

### Post by aquavitae on 2007-07-06
If the error check passes the disk, it should be fine.  Don't know why the md5sum is different though!  Why not just try installing and see what happens, the worst that can happen is you'll be left with a half installed ubuntu, and if you're planning to keep windows this doesn't really matter too much.

---

### Post by keyboardashtray on 2007-07-06
Thank you aquavitae - 

Yes I am very tempted to just go ahead and install - chomping at the bit, in fact. I guess I'm just worried that if something is wrong with the CD, it might not handle the partitioning process correctly, and ultimately screw up everything. I have a recovery disk for my original XP installation, and I don't really have too much important stuff on there. I have a bunch of DVD-Rs for backing up data, but at the moment I am out of CD-Rs, otherwise I'd try burning the Live CD a few more times (although if the md5sums of the 2 I've already burned match each other exactly (but not the original ISO hash), it just seems like I'd get the same result every time.) Ultimately, what I really fear is coming to a situation where I couldn't even boot the Windows Recovery Disc.

If anybody here can point to more info pertaining to the md5sum on the CD itself, that would be great. Otherwise, I guess I should play it patient and wait until I can get to the store and buy more CD-Rs. I've been using Nero, maybe I should download another program to burn it.

Thanks again

---

### Post by keyboardashtray on 2007-07-06
Well after looking even deeper here, I've found an older [thread]("http://ubuntuforums.org/showthread.php?t=480513&highlight=md5sum+CD")  that sounds similar, and a user ruscoe mentions "There are md5s that you can download from the same place as the isos, but those are only good for checking the iso before you burn it."

So it would seem maybe the md5sum hash won't match on the CD after you burn it, or at least the checking program is only good for checking the .iso image pre-burn.

Sadly for me I'd better wait to install or I'll be up all night playing around with it :(

---

### Post by aquavitae on 2007-07-06
I seriously doubt you'll mess up your windows partition!  I assume you're installing on the same drive?  Its generally better to install on a separate drive if you have one, and then you could disconnect windows entirely, but you'd have to have the extra drive.  Its always a good idea to backup your data anyway, and the solution might be to back up your partition table too (I'm not sure how to do this, but I know there are some good guides on the internet)  I can't see any situation where you can't boot the windows recovery disk.  As I see it, the absolute worst case (but highly. highly unlikely) is that the cd will stop in the middle of resizing your windows partition, windows won't boot, and you'll have to reinstall it.  But if you backup your data first, even this isn't too bad. Btw, when I say unlikely, I think its actually impossible.  I may be wrong about this, but I think that before a program in linux starts, it is loaded into memory.  If it is broken, it won't load.  So if the partitioning program (fdisk) is broken, it won't even start, and won't touch your system.  If you're still worried, why not resize your windows partition through windows, so that the worst the ubuntu partitioner can do is to lose your partition table, which, if you first back it up, you can easily restore.

---

### Post by keyboardashtray on 2007-07-06
Yes, thats what I plan to do - use the same hard disk (I don't have a 2nd disk). I've got a 200 GB hard drive and only 42 G is being used atm as it is. I think I'll go ahead and clean up the disc a little more, defragment, backup and all that stuff like you said, and go through [this tutorial]("http://www.psychocats.net/ubuntu/installing"). It seems the simplest one I've seen, and it makes it sound like Ubuntu holds your hand through the whole thing. 

Anyway, thanks again for the support aquavitae, I'm sure I'll be Ubunting in no time.

---

### Post by aquavitae on 2007-07-06
> **keyboardashtray said:**
> It seems the simplest one I've seen, and it makes it sound like Ubuntu holds your hand through the whole thing.
Oh, it does!

---

