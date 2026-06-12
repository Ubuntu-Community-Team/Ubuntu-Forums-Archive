---
title: "LiveCD Install aborts prematurely"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by antmanuk on 2012-07-14
Hello,

Has anyone any experience of the install window vanishing before it completes?

I'm trying to install MythBuntu 12.04 from LiveCD and everything works fine up until the install window just disappears. No error message, nothing. It leaves you staring at the desktop with an endlessly spinning waiting cursor. You can continue to use the desktop as normal. Rebooting just boots into XP on my first partition, confirming the install hasn't completed. There are files on the partition, so it has copied stuff over.

If I refuse to fill in any details in the install screens then the progress bar will fill up nicely and sit there waiting for me. If I proceed to fill in my details, it'll continue to install, at which point the window just vanishes.

Anyone? I even tried installing just Ubuntu, and the same thing happens.

At one point it worked - I don't know what I did, or how I got it working. But my friend broke it so I had to reinstall and haven't succeeded yet.

Help please :)

My system is a Shuttle SN41G2 with AMD 3000+, GeForce 7600 GT. Attempting to install a dual-boot with XP on first partition, then Linux, then swap, then a large NTFS partition.

I have tried many combinations of install options (given visually, at least). No joy.

Thanks,

-Anthony

---

### Post by jmfal on 2012-07-14
Welcome to Ubuntu

Reboot the live cd and run memtest at least 2 passes,

sounds like some bad memory.

---

### Post by antmanuk on 2012-07-14
Thanks!

Memory is fine. This machine's been used for games (things like Fallout 3, Half Life 2, etc) and as a work's PC using XP without issue, so I know the hardware is fine.

The live CD environment works flawlessly with all my hardware, and I can use it to browse, watch 1080P video files, etc.

The problem seems to be more like a software / config issue.

---

### Post by jmfal on 2012-07-14
You might have to go back and make that partition bootable

---

### Post by mikewhatever on 2012-07-14
> **jmfal said:**
> You might have to go back and make that partition bootable

That's a bad idea. It is completely unnecessary, and will, likely make Windows unbootable.

---

### Post by jmfal on 2012-07-14
> mikewhatever 	 		**Re: LiveCD Install aborts prematurely**
 		 	Quote:
 	 	 		 			 				 					Originally Posted by **jmfal** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12103113#post12103113") 				
 				*You might have to go back and make that partition bootable*
 			 		 	 	 
That's a bad idea. It is completely unnecessary, and will, likely make Windows unbootable.

Your right  and I'm sorry 
trying to help another, getting signals crossed
Have t-storms rolling in  have to shut down
Again I'm sorry

---

### Post by antmanuk on 2012-07-14
It's okay, I wouldn't have tried that anyway. I have rebuilt the partitions several times. Just discovered the linux ones were were wrapped inside an extended partition, so I removed that (I only have 4 partitions in total). Made no difference.

Could someone perhaps make sense of the install log? See at which point it gets up to each time. It's confusing to my non-linux brain (I come DOS/Win32).

---

### Post by mikewhatever on 2012-07-14
The log may be useful, but you have to post it.
Hint: use pastebin.com.

---

### Post by efflandt on 2012-07-15
I have been using Ubuntu since 9.04, a week before 9.10 was released, and have never had problems installing from USB or CD before.  But I had issues trying to install 64-bit 12.04 on my laptop from iso on USB after successfully installing same on my desktop to a USB hard drive and then internal drive.  Unfortunately install does not tell you exactly what it is doing and does not have enough error checking to tell when or why it tripped up.

1st 2 attempts on the laptop it never showed the screen to select whether you wanted to copy settings and files from another OS or user, yet it kept attempting NTFS mount my laptop swap partition and failing.  On my desktop sda3 was NTFS, but I had not transferred any settings or files during install, but sda3 on my laptop is swap.

So I rewrote the iso on USB (with Startup Disk Creator) and tried a regular install CD.  Both ran a live system fine like the original USB iso, but just hung forever at about 90% of "Installing system".  But I don't know how to find out what hung or why, unless it is something to do with update-notifier-common.  Example of syslog during install where it hung for over 2 hours without completing:

```
Jul  8 20:13:52 ubuntu ubiquity: Selecting previously unselected package ubuntu-restricted-addons.
Jul  8 20:13:52 ubuntu ubiquity: Unpacking ubuntu-restricted-addons (from .../ubuntu-restricted-addons_12_amd64.deb) ...
Jul  8 20:13:53 ubuntu ubiquity: Processing triggers for man-db ...
Jul  8 20:13:54 ubuntu ubiquity: Processing triggers for doc-base ...
Jul  8 20:13:55 ubuntu ubiquity: Processing 29 changed doc-base files, 1 added doc-base file...
Jul  8 20:13:55 ubuntu ubiquity: Processing triggers for libglib2.0-0 ...
Jul  8 20:13:56 ubuntu ubiquity: Processing triggers for update-notifier-common ...
Jul  8 20:17:01 ubuntu CRON[2712]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 21:17:01 ubuntu CRON[2750]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 22:17:01 ubuntu CRON[2948]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

The resulting system could only boot in recovery mode, and that could not fix incomplete packages because networking could not be enabled (apparently not completely installed yet).

So I downloaded iso for "alternate" install, and that on CD was able to successfully install 64-bit 12.04 which works fine.  So maybe the regular 12.04 install needs some work yet.

---

### Post by antmanuk on 2012-07-15
That's slightly reassuring, thank-you.

It's just odd that it just pre-emptively exists. If it locked the system up, or caused a kernel panic I'd be able to understand it to be some hardware fault. But not even any error. When software just closes (I've been programming for 30 years), it usually means a software problem; as you say, lack of error-checking. My partitions are not regular because I had 4 NTFS partitions in XP, I deleted the middle two so I could make way for linux partitions.

Incidentally I am installing the 32-bit iso from CD. Installing OpenELEC from USB causes an instant kernel panic at boot, so I wasn't going to bother with a live session from USB.

I'll get log files posted when I make another attempt. I've taken a break on it to work on the garden on the one day in ages we haven't had rain. England hasn't been granted a summer this year :(

---

