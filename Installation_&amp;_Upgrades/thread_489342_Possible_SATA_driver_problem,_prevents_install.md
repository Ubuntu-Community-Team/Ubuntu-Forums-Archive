---
title: "Possible SATA driver problem, prevents install?"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by trentend on 2007-07-01
I have had an ongoing [saga]("http://ubuntuforums.org/showthread.php?t=475539"), attempting to get Ununtu 64 7.04 (or indeed any!) installed on a new machine.  It is inteded to be a dedicate ubuntu desktop machine with no other operating system.

ECS KN3 SL12 Extreme Motherboard (nForce 590)
Western Digital WD5000AAKS 500GB SATA II 7200RPM 16MB Cache in an [ICY Dock MB-453SPF Backplane]("http://www.raidsonic.de/en/pages/products/backplanes.php?we_objectID=4250")
4 Gb RAM
3800 AM2 Dual Core Athlon 64

I'm using the (hotswap?) backplane with the hope of adding a couple of further drives to extend the capacity of the machine.  Would probably look be able to swap in and out various drives over time.  Currently just the one drive installed.

As documented on the above thread, I have been unable to make a working install, and indeed currently any sort of install.

In order to try to understand what is going wrong I booted using the current Knoppix CD.  This seemed to autodetect everything well, but when attempting to read the hard drive (sda1) I can hear drive noises, but the machine essentially freezes.  It can read the directory structure, but any attempt to manage the files causes a failure.  This would presumably be consistent with my previous attempts to update/upgrade, and indeed the multiple failures when installing.

I'm no Linux expert, being a relative newbie, but have a high level of experience of computers in general.  I have a huge stack of correctly burned install CD's, of all flavours.  Trust me when I say that it's not a coaster problem.

So, is it possible it's a SATA HD/Backplane driver problem?  If so, any suggestions?

I really, really, want to run Ubuntu on this machine.  It's why I built it.

Any help or suggestions much appreciated.

---

### Post by Pumalite on 2007-07-01
Sounds like a hardware problem. Check connections. Your hard drive might be dying. Maybe there is a problem with the installation of the hard drive? A SATA drive, working alone, should be no problem for Ubuntu.

---

### Post by trentend on 2007-07-01
> **Pumalite said:**
> Sounds like a hardware problem. Check connections. Your hard drive might be dying. Maybe there is a problem with the installation of the hard drive? A SATA drive, working alone, should be no problem for Ubuntu.

Is it possible the backplane introduces a problem?  I wouldn't have thought so, but it's worth mentioning.  I've been and checked the connections, but I'll do it again.  All the hardware is new.  I appreciate that doesn't exclude failure, but it honestly doesn't feel, like that.  Knoppix does a very good job (I realise it's an acknowledged strength of it) of recognising all hardware and installing (at least the live version) from the CD.  Ubuntu isn't getting that far.  I'm having freezes, debootstrap errors, and on the odd occasion that an install completes I can't update or upgrade.  Is this consistent with a hard drive problem?

---

### Post by Pumalite on 2007-07-01
What about the noises you said you heard? Is that software? Or did you mean you heard the drive 'working'? You make no mention of it, but I would do a couple of things. check your iso, check your CD, do checksum. If you have to download again; torrent is better than HTTP or FTP

---

### Post by trentend on 2007-07-01
> **Pumalite said:**
> What about the noises you said you heard? Is that software? Or did you mean you heard the drive 'working'? You make no mention of it, but I would do a couple of things. check your iso, check your CD, do checksum. If you have to download again; torrent is better than HTTP or FTP

I can hear interference from the hard drive over the speakers - not the physical clicking, electromagnetic interference.  It's not unprecedented, I've been able to hear that in many machines before.  On the CD thing, trust me, I have that so covered.  I have a whole stack of CD's all from different torrent downloads, checksum verified, burnt, verified, CD verified by install programme.  It's possible one or two might have slipped through this net, but I have tried tens of times over two weeks (and I've used different computers for the download and burning just in case, along with three different CD writers).

Perhaps I should have mentioned that I have 7600 GT video card, but I honestly don't think that has any bearing on this issue...

---

### Post by Pumalite on 2007-07-01
You have excellent hardware and Ubuntu should have no problem with it, that I'm aware of. I'm at a loss as to what else to suggest. Maybe somebody else will jump in. Good luck.

---

### Post by trentend on 2007-07-01
Okay.  I've stripped the machine down, reseated the memory, unplugged, cleaned, and reconnected all the plugs and connections.  I've checked all the fans, temperatures, bios settings.  I've also added another connector lead to the power supply to spread the demand over as many leads as possible (I have a nice xclio x14 s4p3 550W power supply with removeable cables).

I found that the header for the front case USB ports wasn't grounded for both ports (2x5 pin connectors, instead of 2x4 pin plus common ground) - so I modified with a piece of wire (the usb ports appeared to work fine before, and appeared to work fine afterwards...).

Then I reassembled, and rebooted using the 7.04 Fiesty Live CD install, with noapic and xforecevesa switches added, and the "quiet" switch removed.

Installation seemed to work perfectly, and the machine rebooted into the installed operating system.  The file system is readable, and I created some documents using openoffice and saved them successfully to home. Everything appears to be fine.

I have, exactly the situation that I reported in the other thread:

"The best that I can possibly do is with the 64bit desktop, and with xforcevesa and noapic switches (for example if I add the nolapic switch the installation always fails somewhere in the late 50%'s with a quick beep and then back to the live CD.

With this best case installation the situation is exactly what I have previously described. Any attempt to use the update manager, or sudo apt-get update, or the restricted drivers (nvidia) handgs the machine and stops it from working. If I don't attempt to do any of this (or install any additional packages) the installation appears fine and all the software seems to work as expected.

if I type (in the terminal):

sudo apt-get update

the command gets to 95% and then fails with the following message:

message from syslogd@machine at time/date Machine kernel:[ 262.486850]Oops 0011[2]SMP

message from syslogd@machine at time/date Machine kernel:[ 262.487218]CR2 ffff8100010091b8

this is rock solid repeatable."

The machine generally continues to work,  and will shutdown or reboot.  I don't have the requisite experience, but all my instincts point to a software error, probably in the kernel (particularly given the message above).

I'm completely stuck.  I've tried every suggestion made to get past this point.

Any help for this hapless (virutal)newbie, much appreciated.

---

