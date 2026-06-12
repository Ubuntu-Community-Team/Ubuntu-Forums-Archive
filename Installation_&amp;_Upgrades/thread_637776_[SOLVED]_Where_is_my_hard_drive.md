---
title: "[SOLVED] Where is my hard drive?"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by amckenzie on 2007-12-11
I'm trying to install 7.10;  I've used a number of others (most recently I installed 7.04, I think, on my laptop, which worked perfectly.

So.  I ran into the "black screen on the LiveCD" problem.  That was solved by replacing "quiet splash" with "nosplash", and specifying 1024x768 at 16 for boot parameters.

Now I've got another problem;  the installer doesn't detect my hard drive.  It's a standard PATA 80GB drive.  So far I've built one partition while installing windows (it's a work computer, and I need WinXP for occasional testing), but neither GParted, the installer, nor anything else (even fdisk!) seem to detect the drive.

Anyone know what's going on here?  I'm really disappointed by this... it seems like a big step backwards.

---

### Post by ken_vh on 2007-12-11
Not that I have any clue, but it might be helpful if you put your HDD and mainboard type in your startpost.

---

### Post by amckenzie on 2007-12-11
Probably true... sorry about that.

The motherboard is an Asus P4S800-MX, and the drive is an 80GB ATA drive;  I think it's a Western Digital.  I've been running Ubuntu on it for about a year, and this is the first time I've had problems.

I've also just been going through dmesg, and found the message "ata1: SRST failed (errno=-16)", which I failed to notice before.

After doing some research on that, it looks like the problem may be that the new sata drivers aren't correctly supporting my older pata drive.

---

### Post by ken_vh on 2007-12-11
Check this out:
[http://www.redhat.com/archives/fedora-list/2006-October/msg04082.html](http://www.redhat.com/archives/fedora-list/2006-October/msg04082.html)

> 

Regarding the excessively long boot times and timeout errors
from the ata_piix module...

In case enybody reading this didn't catch it in a different thread
on this mailing list, Bob Chiodini provided a possible solution or
workaround.  It disables the SATA drive probing, which is
particularly useful on systems that don't support SATA but that
the kernel thinks does (of which the Dell Optiplex GX270 is
known to exhibit this annoying behavior).  Here's what Bob said:

> ... did some tweaking to /etc/modprobe.conf and this might
> avoid the ata_piix timeouts during boot and/or udev init.
> 
> Add or modify as follows:
> 
> alias scsi_hostadapter ata_piix
> options ata_piix noprobe
> 
> As long as you do not have SATA drives.
> 
> This was tested on a Dell GX270

Of course this only applies once you have FC6 installed (or
after upgrading to the latest FC5 kernel).  If you're in the
process of doing the FC6 install, just be patient--the timeouts
will take a couple minutes, but they will pass and it will cause
no harm.

Thanks Bob.
--
Deron Meranda


I hope it helps :)

[edit] By the by: "SRST failed (errno=-16)"  with the quotes gave me the best Google search results.

---

### Post by amckenzie on 2007-12-11
Ken,

  I'd found that, but the problem is that I can't install at all;  would entering the "ata_piix noprobe" as a boot option work?  (I'm not near that computer at the moment, though I can try tomorrow, or possibly later today...)

Thanks!

---

### Post by ken_vh on 2007-12-11
> **amckenzie said:**
> Ken,

  I'd found that, but the problem is that I can't install at all;  would entering the "ata_piix noprobe" as a boot option work?  (I'm not near that computer at the moment, though I can try tomorrow, or possibly later today...)

Thanks!

That's probably not going to work. I'm afraid I have no clues left...

---

### Post by amckenzie on 2007-12-12
I'm pretty much out of options myself... I've installed from 6.10 (I had the CD lying around) and upgraded to 7.10, but I'm pretty disappointed by this failure.  I have a pretty basic computer (2GHz celeron, 512MB of RAM, 80GB hard drive) -- this is something that ought to just work.  

(Though I'm in the process of rebooting, and it looks like the upgrade to 7.10 broke something... so maybe I'll be going back to LTS for now.  Or back to a different distro.)

---

### Post by amckenzie on 2007-12-13
This is solved!

Someone on a mailing list pointed out this thread:  [http://ubuntuforums.org/showthread.php?t=586894&page=4](http://ubuntuforums.org/showthread.php?t=586894&page=4)

Switching the drive to Single Drive mode (no jumper) fixed the problem.

It looks like the problem is a Western Digital drive with a motherboard using the SiS chipset.

Hope this helps someone else who's having the same problem!

---

### Post by mozetti on 2007-12-13
It was under the sofa cushions, wasn't it? *Everything* ends up under those damn sofa cushions. :lol:

Glad you got it sorted out.

---

### Post by amckenzie on 2007-12-13
> **mozetti said:**
> It was under the sofa cushions, wasn't it? *Everything* ends up under those damn sofa cushions. :lol:

Glad you got it sorted out.

Well, there /were/ quite a lot of dust bunnies involved....

Thanks!

---

### Post by ken_vh on 2007-12-14
I'm happy to see your problem resolved!
What a strange solution, I'll definitely remember it.

Have fun with your OS :)

---

### Post by amckenzie on 2007-12-14
Two other points worth mentioning on this one:

1)  Grub, even in the versions that installed correctly, was EXTREMELY slow.  Five to ten minutes from the point where grub started to the point where I could actually select a system to install, usually on the ten minute end of the scale.  With the drive set to "single", it runs full speed.

2)  Installing 6.10 and upgrading worked fine, except that the newest kernel (installed with 7.10 during the upgrade) didn't work at all.  Re-selecting the older kernel "solved" that problem (it allowed me to boot), but I never got it working with 2.6.22-14-generic.


Now, off to get myself a 7.10 install from CD, rather than via update!

---

