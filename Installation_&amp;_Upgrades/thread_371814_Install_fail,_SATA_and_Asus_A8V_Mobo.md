---
title: "Install fail, SATA and Asus A8V Mobo"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by Strider42 on 2007-02-27
Hi,

I'm having real problems installing Ubuntu 6.10 Edgy on my system.  After
 having a really successful install with my Dell Inspiron I thought going to Ubuntu on my main box would be a breeze.  How wrong.  Having checked all the related threads on the site I'm still no nearer to fixing the problem.

Current config is:

Asus A8V
AMD 64 3000
512 Mb RAM
2 x 80Gb Maxtor SATA drives (no raid)
GeForce 5200 - 256Mb

I'm using the Edgy 6.10 AMD Alternative installation disk, but the install program fails to see my two hard drives.

During boot I get the following messages:

ata1: failed to set xfermode (err_mask=0x4)
ata2: failed to set xfermode (err_mask=0x4)

The install then continues and when we get to the disk partition screen it says no hard disk detected.

Any ideas?  I'm rather new to Linux so it just might be I'm missing a fundamental step in the install process.

Thanks in advance
Paul.

---

### Post by halfvolle melk on 2007-02-27
Probably a problem with the chip set, more specifically the sata controller. I suggest you search the forums for the chip set and / or mobo.
[http://ubuntuforums.org/showthread.php?t=296700](http://ubuntuforums.org/showthread.php?t=296700)
[http://ubuntuforums.org/showthread.php?t=361427](http://ubuntuforums.org/showthread.php?t=361427)

---

### Post by Strider42 on 2007-02-27
Yes,  I read those two threads but it doesn't help me.  I only have the two SATA drives and no IDE drive, but the install just doesn't see the drives.  It thinks the system is drive less. 

I'll remove the 2nd SATA in the morning and try installing with just the one to see if that helps any - though I fear it is more likely a chipset issue.  If that's the case it is back to XP for the time being and I'll have to be content with the laptop running Linux.

Thanks for the input.

---

### Post by joeindo on 2007-02-27
Have you enabled the sata boot rom in bios? In bios - go to advanced - onboard devices - enable either the promise onboard controller or the via controller...

I'm experiencing a different problem with my A8V board:

[http://www.ubuntuforums.org/showthread.php?t=371515](http://www.ubuntuforums.org/showthread.php?t=371515)

---

### Post by joeindo on 2007-02-27
One other thought... The A8V I own only supports data transfer of 1.5/sec... Many sata hard drives are default jumpered to 3.0 - have you checked your drive's jumpers and throttled the drives down to 1.5/sec ?

---

### Post by Strider42 on 2007-02-28
Hi Joe,

Yep, boot Rom is enabled.  I'll check out those jumpers and post back if it makes a difference.

---

### Post by Strider42 on 2007-02-28
OK, just to keep the thread up-to-date.  The drives were jumpered for 150 and I have removed one drive from the system, but still Ubuntu doesn't find the drive.

So, I'll have to wait for a different box to come along at some point - so as disappointing as it is, it's back to XP.

---

### Post by Strider42 on 2007-02-28
OK, some success here.

I used the 'fix broken installation' option on the AMD Alternative disk and it found the drive and proceeded to install 6.10 Edgy.

But :(  on reboot it stalls.  I have run the boot sequence in recovery mode and it flies along finding all the hardware, and then stalls after the word Done, with the following:

Begin: Waiting for root file system...

and here it sits, and sits, until I get the message.

ALERT! /dev/hda1 does not exist.  Dropping to a shell!

then the /bin/sh: can't access tty; job control turned off

Why is it looking for hda1, I thought the SATA drive was tagged with sda?  Is that not the case.  If so, how do I get the boot sequence to find sda?

Many thanks

---

### Post by Strider42 on 2007-02-28
OK, Much progress :)  Yes, yes, yes :guitar: 

I edited the boot commands so that hda1 now reads sda1 and it boots now to a command line.

I get to root@paul-desktop:/#

So how do I get the Gnome desktop to launch from here? SCRUB THIS _ SORTED

One other question, how do I edit the boot file so that I can change /dev/hda1 to /dev/sda1 permanently? SCRUB THIS_SORTED

Many thanks for the help.

Cheers
Paul

---

### Post by thecrumb on 2007-03-01
Where did you edit and replace the hda with sda?

I'm having similar problems and am stuck...

Thanks,
Jim

---

### Post by joeindo on 2007-03-02
Jim aka thecrumb,

You can edit the boot menu options right off of the boot menu - select "e" to edit... The options should be at the bottom of the menu.

---

