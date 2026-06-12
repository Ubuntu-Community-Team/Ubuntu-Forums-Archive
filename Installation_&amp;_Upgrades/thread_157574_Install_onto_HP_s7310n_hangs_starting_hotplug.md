---
title: "Install onto HP s7310n hangs starting hotplug"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by beowabbit on 2006-04-09
Hi.  I'm trying to install Breezy on an HP Pavilion Slimline s7310n PC.  The install hangs (after the reboot) at "Starting hotplug subsystem".  (Trying to boot from the Live CD hangs at the same place.)  Googling for that found nothing relevant to my particular hardware, but one person said he'd had USB problems that caused that, so I turned off probing for USB devices with debian-installer/probe/usb=false (or whatever the correct syntax is; I don't have the GRUB help-screens in front of me right now), but I got the same thing.

(Incidentally, my keyboard and mouse are USB, because I have this on a USB KVM.  They work fine in GRUB and the installer, although interestingly they did *not* work in Windows before I wiped it.)

So, (1) has anybody succeeded in installing Ubuntu on this hardware, (2) does anybody have ideas for what might be causing this problem, and (3) is there any way to turn off hotplug in the installer?  (Booting with "expert" didn't seem to give me an option not to use hotplug.)

I will want to use the internal card reader and an 802.11b USB dongle, so it would be nice to have hotplug working, but I'll settle for having the thing successfully boot to a login screen as a start.

---

### Post by beowabbit on 2006-04-11
I found [this message]("http://ubuntuforums.org/showthread.php?t=117011") about similar problems on a different model of HP, and that led me to try disabling the sound card in the BIOS.  Sure enough, that let me install.

I care about being able to use the on-board sound support, but at least this will let me bring the machine up enough to do further diagnosis; maybe it's not actually the driver for this sound chipset that's causing the problem, but something else that's being probed for.

---

### Post by brucenduane on 2006-04-14
I have installed Ubuntu 5.10 Breezy on Duane's HP Pavilion Slimline s7320n and got it past the hang on hotplug by following the advice  of  **tucoz**  on
[http://www.ubuntuforums.org/archive/index.php/t-75181.html](http://www.ubuntuforums.org/archive/index.php/t-75181.html)

The 7320 is the same as the 7310 with 200 vs 160 Gig Hard Drive and 1.0 Gig vs 0.5 Gig of memory.   The rest of the box is the same.   I got the computer running Ubuntu without sound.   I read on the web that this may be fixed in Ubuntu 6xx but have been unable to install the Live CD of Dapper Flight6 and get it run. 

The   tucoz's advice was to edit the hotplub blacklist file
/etc/hotplug/blacklist

Go to the bottom of the file and add the two lines

snd_hda_intel
snd_hda_codec

Save the file and reboot Ubuntu.  I used Knoppix 4.0.2 to be able to make the file changes as I have that linux laying around.   Other than not having sound, the system runs great.  Hope this helps you and is in time for you to use.

Some useful URLs on this
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15465](http://bugzilla.ubuntu.com/show_bug.cgi?id=15465)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15031](http://bugzilla.ubuntu.com/show_bug.cgi?id=15031)
[http://www.ubuntuforums.org/archive/index.php/t-76138.html](http://www.ubuntuforums.org/archive/index.php/t-76138.html)

Bruce (and Duane).

---

### Post by beowabbit on 2006-04-22
I'm happy to say that the beta of Dapper Drake installed smoothly on the s7310n, and has working audio.  (I get no sound out the front-panel headphone jack, but the rear line-out jack works fine.)

---

