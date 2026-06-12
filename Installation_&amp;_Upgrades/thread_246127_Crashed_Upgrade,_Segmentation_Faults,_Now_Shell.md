---
title: "Crashed Upgrade, Segmentation Faults, Now Shell"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by James_Nostack on 2006-08-28
I've run into major problems upgrading from 5.10 to 6.06.  I get a million segmentation faults during boot-up, and feel very frustrated.  I'm not even sure I know the right questions to ask.  (Hopefully my experience will help teach people what NOT to do!)

* I use a Toshiba Satellite laptop, which overheats a lot.
* I've been using Ubuntu 5.10 for almost a year.
* I decided to upgrade to 6.06 this morning.
* I backed up my critical files first... 
* ...but I was too miserly with what I considered "critical"
* about 1220 files were downloaded
* the laptop overheated while applying changes, and crashed

At this point, I should have gone to the forums, because I was out of my depth and knew it.  But, like an idiot, I tried things wildly, and made the situation much worse.

* After the crash, the computer booted to the desktop.
* Some packages were installed--there was a network icon in the upper right of the screen.
* I tried to finish the upgrade with Synaptic, but it didn't work
* I tried to finish the upgrade with Update Manager.
* Update Manager said that a bunch of packages would have to wait for me to use "sudo apt-get dist-upgrade", but it would work on the others.

For some reason I forget, Update Manager didn't finish the job, and I had to go into the terminal to fix a package.  I think the arguments were --configure -f, but I don't remember what I was doing.  I should have written it down!

* Sometime during this, it must have overheated, and crashed.
* When I boot up, Grub 1.5 loads...
* It tries to boot Linux...
* And runs into a million segmentation faults.

The error message I get now is....


```
ALERT!  /dev/hda1 does not exist.  Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#
```

Is there anything I can do to...
* preserve my old files
* and get back to either 5.10 or 6.06?

=====
My recommendations based on this experience (I'm sure everyone knows these, but it can't hurt to see it again):

1.  Always back up every file you care about.  If you'd be sad if you lost it, it's "critical."  

2.  At the first sign of trouble, go to the forums.  Don't make things worse.

3.  If you start screwing around, write down what you're doing, so you'll remember what worked, and what didn't.

---

### Post by James_Nostack on 2006-08-29
(bump)

---

### Post by Fatjoint on 2006-08-29
Pretty much at this point, I'd use the live CD and get the rest of the files that you were looking for.

Then start over.

Someone else may be of more help, but I'm thinking it's pretty much too mixed and matched at this point.  I ran into a similar issue going from 5.10 -> 6.06, so I wiped everything but my /home.

---

### Post by James_Nostack on 2006-08-29
Thanks, I'll give that a shot!  I appreciate the help.

Just so I understand what's involved: the live-CD I have on hand is, I think, 5.04.  If possible, I'll rescue the extra files. 

Can I run the upgrade to 6.06 from the 5.04 live-CD, or will I need a 6.06 install CD?

---

### Post by James_Nostack on 2006-08-29
Hmm... the 5.04 live CD doesn't seem to work.  The CD light blinks for a little while, and there are noises.  The screen is blank except for a blinking _ mark.  And then it goes into the same segmentation fault and error message as before.

I'm going to try to burn a 6.06 live CD, and see what happens; maybe my 5.04 live CD is faulty somehow.

If I have to use a 6.06 Install CD, is there a way to protect my old /home ?

---

### Post by James_Nostack on 2006-08-29
Okay, the 6.06 Live CD doesn't work.  (Maybe I should use the Alternate Install CD?)

---

### Post by hakre on 2006-08-30
Do you get any error with the live CD / have you checked another Bootable CD you know that was working with your computer?

Do you have got a floppy Drive or a Bootable USB Port on that computer?

I Remember a Toshiba Satellite laptop that was install "fixed" with Ubuntu for being able to welcome a Knoppix installation. Maybe it works the other way round as well and you can try out with a knoppix live CD?

---

### Post by James_Nostack on 2006-08-30
> Do you get any error with the live CD

No.  The screen goes blank, the CD makes a couple of "lazy" noises (i.e., the CD is spinning but not doing much).  After maybe 5 minutes, it goes to Grub 1.5, tries to boot, and runs into thousands of segmentation faults.  (Without the CD, it does this right away.)


> have you checked another Bootable CD you know that was working with your computer?

It did this with the Ubuntu 5.04 Live CD, and the 6.06 Dapper CD.  I don't have any other bootable CD's.

> Do you have . . . a Bootable USB Port on that computer? 

I have several USB ports, but no USB boot disks.  Also, I don't know how to tell the computer to look at the USB port first, instead of booting off the hard drive.  (I have been pressing Ctrl-C when booting from CD, b/c I think that worked when I used Windows.  But I am not sure if that's correct.)

Thanks for the response though!  I wish I could get this to work...

---

