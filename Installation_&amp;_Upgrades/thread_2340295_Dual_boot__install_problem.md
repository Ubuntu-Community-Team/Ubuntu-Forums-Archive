---
title: "Dual boot / install problem"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2016-10-17
I've read multiple thread & sources on installing Ubuntu along side Windows 8.0 or newer. And am still perplexed on what my problem is. In short, here's what I've done:

- HD with OEM Windows 8.0 installed
- Used Windows to shrink disk C: 
- Booted Ubuntu 16.04 from USB, and used gparted to create new ext4 partitions
- When attempting to install Ubuntu from USB, it STILL doesn't see Windows (or any of the partitions) and shows only option as installing on all of /sda.
- I've tried many/all combinations of UEFI, secure boot, and fast boot. But mostly: UEFI on, Fast Boot off, and have tried both secure boot on and off.
- Gparted gives all sorts of ignore/warning pop ups.
- Ug.

Thoughts?

---

### Post by oldfred on 2016-10-17
Did you turn fast start up or always on hibernation off?
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold) 

More info on UEFI install on link in my signature below.

---

### Post by aeronutt on 2016-10-17
Yes, fast start up is turned off.

Making a dual boot install of Ubuntu so difficult is certainly hurting ubuntu'ss case for wide acceptance.

Here's what the install screen looks like when it doesn't see Windows:
[img]http://i.imgur.com/VYILVSV.jpg[/img]

A few of the odd pop up warnings from gparted:
[img]http://i.imgur.com/i4ugr0H.jpg[/img]

[img]http://i.imgur.com/z5C2Crr.jpg[/img]

Gparted sees the partitions though:
[img]http://i.imgur.com/8pj22ai.jpg[/img]

---

### Post by oldfred on 2016-10-17
Some Windows tools have used the uncommon 2048 sector setting which creates issues.
Most new drives are really 4096, but use 512 logical.

You seem to have several drives as messages post refer to sdc, sdb, then sda. Also please post images as attachments not in line.
Easy to add screen shots with forum's advanced editor and paperclip icon.

Post this for each drive, sda, sdb, sdc, particularly drive you want Ubuntu installed on.

sudo gparted -l /dev/sda

---

### Post by aeronutt on 2016-10-17
I'm bouncing between a USB boot, taking pics with my phone, and then back to windows to post here...so getting a screenshot isn't simple. I'll do the best I can and will try to use 'attachments'. Although the pics I posted are hosted via imgur.

Anyway, "sudo gparted -l /dev/sda " responded with something like "-l drive not found"...so gparted didn't recognize that switch. Man gparted didn't help. Otherwise, it's the same as the pic above for /sda.  sdb and sdc are internal solid state (32GB IIRC) and the USB drive.

Just realized, you may have meant 'sudo parted -l ...".  I'll run that and post.

---

### Post by aeronutt on 2016-10-17
Ok, here's "sudo parted -l /dev/sda"

[http://imgur.com/X9xF4gK]("http://imgur.com/X9xF4gK")

[http://imgur.com/UNMtkrt]("http://imgur.com/UNMtkrt")

Also, in BIOS, SATA is set to 'intel smart response technology'. I considered switching to ACHI, but got warnings about possibly corrupting data.

---

### Post by oldfred on 2016-10-17
If the other warnings are just your flash drives, I think you can ignore them.

But you need to run the fix on your sda drive.
Either use gdisk or parted and accept the fixes.

---

### Post by RobGoss on 2016-10-17
When you try to setup a dual boot with  Windows and Ubuntu and run the live installer are you presented with the option to install alongside Ubuntu?

---

### Post by aeronutt on 2016-10-17
> **RobGoss said:**
> When you try to setup a dual boot with  Windows and Ubuntu and run the live installer are you presented with the option to install alongside Ubuntu?

Nope, that's the problem I'm running into. It's showing this when I get to the 'where to install' option:

[http://imgur.com/VYILVSV]("http://imgur.com/VYILVSV")

---

### Post by oldfred on 2016-10-17
But that is showing sdc, not sda?
What brand/model system?
Is sda anything special like Intel SRT which is seen as RAID, drives need to be set to AHCI in UEFI/BIOS.
Or a new NVMe SSD?

Can you create partitions on sda with gparted?

---

### Post by RobGoss on 2016-10-17
Looking at those screen shot you posted in the** 3#** post it looks like there are a few Linux partitions already installed on that machine is this so?

---

### Post by aeronutt on 2016-10-18
> **oldfred said:**
> But that is showing sdc, not sda?
What brand/model system?
Is sda anything special like Intel SRT which is seen as RAID, drives need to be set to AHCI in UEFI/BIOS.
Or a new NVMe SSD?

Can you create partitions on sda with gparted?

Yea, weird huh. Gparted would show all partitions, but the install program would only show sdc (the USB flash drive) !

---

### Post by aeronutt on 2016-10-18
> **RobGoss said:**
> Looking at those screen shot you posted in the** 3#** post it looks like there are a few Linux partitions already installed on that machine is this so?

Yes, I added partitions using gparted (from a USB boot).

Ok, update.

I ran parted on sda, and allowed it to fix all the problems it found, which was only 1. (Something about unused space.)

THEN, ran the installer and everything is working. I can boot into multiple OS's, including Windows 8.0. 

An odd thing is, now when I run gparted again, it's showing up that 'unused space' warning again. WTF? But it's all working.

Thanks for all the help, I'll mark as solved (magically).

---

