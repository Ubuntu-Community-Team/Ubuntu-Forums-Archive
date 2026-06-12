---
title: "Hardy liveCD Hangs After Loading Kernel"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by thethimble on 2008-04-26
The CD boots and asks me which option I want (LiveCD, Install, Check for CD Defects, etc.). Which ever option I choose, a progress bar saying "loading Linux kernel" shows up, moves to 100%, then leaves me with a blank, black screen with a flashing text cursor at the top left.

I've tried everything... gg/hh, livecd/text, desktop/server, x86/64...

The same thing always happens. This can't be a problem with a corrupt image/cd because I've tried multiple times with multiple burners. I've checked the MD5 sums on all of my ISOs and burned at 4x every time.

Thanks in advance!

---

### Post by Ilan on 2008-04-26
not your CD. Have same problem with my old desktop (Pentium III) and also installation freezes, but the CD works fine on my laptop.
Perhaps it has to do with the graphics card.

---

### Post by thethimble on 2008-04-26
I have an ATI Radeon 9800.

I tried installing without it (using onboard Intel graphics) but the same thing happened.

---

### Post by victor9098 on 2008-04-26
I have been having a similar problem, here is my thread for details:

[http://ubuntuforums.org/showthread.php?t=768539](http://ubuntuforums.org/showthread.php?t=768539)

Do we report this as a bug?

---

### Post by XVII on 2008-04-26
> **victor9098 said:**
> I have been having a similar problem, here is my thread for details:

[http://ubuntuforums.org/showthread.php?t=768539](http://ubuntuforums.org/showthread.php?t=768539)

Do we report this as a bug?

Report a bug through the [Ubuntu Launchpad]("https://launchpad.net/ubuntu").

---

### Post by mathenge on 2008-04-26
You might be having problems with ACPI. There are boot options that you can try when the live-cd gives you the boot prompt.

Press ESC.

One you can try is acpi=off

Or noapic

I believe you can list them when you get the prompt.

---

### Post by victor9098 on 2008-04-26
Silly question...but...what is the ACPI and why would it be giving me trouble with this version of Ubuntu?

So when I insert the CD and get to the screen with all the options for what to do (i.e. install, test cd, etc...) I then press 'esc' and go into the ACPI options?

Any other instructions? Would be great!

Thank you

---

### Post by thethimble on 2008-04-27
I tried "live acpi=off" but the same thing happened. Here's what it says whether I try "live", "live-install", or "live acpi=off":

> Loading /casper/vimlinuz .................
Loading /casper/initrd.gz ...............

After this, the screen clears and the flashing cursor returns to the top left of the screen. :(

---

### Post by thethimble on 2008-04-27
On a side note, I tried booting ubuntu 5.10 and it worked perfectly fine. Any ideas?

---

### Post by victor9098 on 2008-04-27
Same thing with me, no luck booting with 8.04 no matter what method I use! Put in 7.10 and it works first time, just finished getting my system back to how she was.

---

### Post by thethimble on 2008-04-27
I tried booting 7.04. The same thing happens, except I get "CRC Error - System halted"

No error shows up for 7.10 but I get a blank screen with a flashing cursor...

This is SO frustrating...

---

### Post by dascribe on 2008-04-27
I am certainly new to Ubuntu and Linux Distros in general, but I have come across this same problem. My screen goes blank with a blinking cursor up in the top left. I left it there for about an hour thinking it would do something, but it didn't.

I am trying to install on an older HP Pavilion N5440 Laptop Pentium III. I am good at reading so if there is more info elsewhere I will gladly read it if it helps me get my first taste of Ubuntu.

---

### Post by thethimble on 2008-04-30
_Problem Solved!!_

My failing installation attempts have ALL been due to bad disks... I guess my burner just sucks...

I took my burned disks and tried to unpack /casper/initrd.gz on another machine. After I got different errors (premature eof, unrecognized, crc, etc.) I realized that the disks were bad. I tried verifying my disks using imgburn and sure enough, there were 100+ errors per disk :(

I burned the same cd on a friend's computer and it ended up working.

If you are having this problem, download [imgburn]("http://www.imgburn.com/index.php?act=download") and try verifying your burned disk(s). Most likely you will find an error.

---

### Post by Mr_B on 2008-05-05
I had the same problem after I had SUCCESSFULLY installed Hardy on my laptop. Because the battery estimate said something like 57 hours remaining (Yea, I wish!) I decided to let the battery run out so I would have a more accurate estimate in the future. After the battery died the computer would not boot up. It would not even boot from the live CD - which I know was good!
Which ever boot option I picked, the progress bar said "loading Linux kernel", it moved to 100%, then I got a blank, black screen with a flashing text cursor in the top left.

I ended up booting with an Ultimate Boot CD 4 Windows ([http://www.ubcd4win.com/](http://www.ubcd4win.com/)) and deleting my Hardy OS partition. NOW the live Hardy CD booted fine and I re-installed without any problems. I had fortunately partitioned my /home as a separate partition so I did not lose any of my settings, pictures, or music.
I did see a message "unattached inode 3850430; fsck died with exit status 4"

It looks like the Hardy boot hangs when trying to mount a corrupt Ext3 file system. This happens whether trying to boot from HD or live CD. I would call this a big flaw/bug!

---

### Post by Rocky37 on 2008-05-06
> **Mr_B said:**
> I had the same problem after I had SUCCESSFULLY installed Hardy on my laptop. 

 I would call this a big flaw/bug!

In the same boat here: laptop was a breeze to load, desktop is a bitch!

Trashed my XP boot the other day trying to load gutsy 7.1 alt disk. Hate when that happens!

I'm running a 4 year old home built with pentium 4 on a foxcomm FX4MR-ES motherboard, 4GB ram, an older sound blaster 5.1 Live and Radeon 7200 video card, seagate barracuda 250gb ,seagate 80gb and a maxtor 89gb ---- am thinking of replacing the audio and video cards and see if that helps.

I have been wanting to move into linux for over a year.  I've had it with Microsoft!  Hardy has been a breath of fresh air on my laptop and am now using as my main OS.  I'm bound and determined to get Hardy up and running on the desktop!!!

---

