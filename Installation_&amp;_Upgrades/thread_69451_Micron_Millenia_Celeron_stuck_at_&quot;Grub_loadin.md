---
title: "Micron Millenia Celeron stuck at &quot;Grub loading, please wait...&quot;"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by NomadOfNorad on 2005-09-26
Well, for the time being I gave up on the matter I mentioned in this thread:

"Grub stage 1.5 gives error 15 "[http://ubuntuforums.org/showthread.php?p=371555]("http://ubuntuforums.org/showthread.php?p=371555#post371555")

...and let the 5.04 "Hoary Hedgehog" release i386 live-CD do a standard, from scratch, generic, wipe-the-hard-drive-and-repartition, automatic install. It gave me approximately a 9.8 GB partition for \ and a 450-something MB swap file, and went all the way through the install to the part where you remove the CD and let it reboot so you can log on for the first time.

It rebooted, and got as far as:

[B]GRUB loading stage 1.5...

GRUB loading, please wait...
_
[/B]

And then it just sits there, with the floppy-drive access light staying on indefinately, even though this wasn't a floppy-based install...

This time it didn't give *any* kind of error number, it just hung.

I have tried several different Linux distros on this machine. First one was ClarkConnect HOME 3.1, second one was TinySofa server, both of which failed to install functionally onto the machine, due to Grub issues. I tried one or two other live-CDs which didn't even boot right. I tried the Ubuntu live CD, it it booted nicely there but, as you can see, I can't get it to install.

I am tearing my hair out over this. I've got other old machines here, but none of them have as much RAM as this one does (well, actually, *one* does), and I don't want to lose the existing Windoze install of of any of them, either.

I **desperately** need to set up a dedicated email machine, like ***yesterday***!!!  I don't have **time** to bang my head against a wall for weeks and weeks trying to puzzle out why this machine does ***not*** seem to like having Linux installed onto it...

Does anyone know why this machine hangs at launch now?  Is there something I should be looking for in the BIOS settings?

The bios comes up as:

[B]ROM PCI/ISA BIOS VERSION 2.71 (2A69KB3F)
SMOS SETUP UTILITY
AWARD SOFTWARE, INC.
[/B]
Poking around in all the screens there, I don't see any obvious issues. I remember one other old BIOS I came across that explicetly had a flag to set for if this was a Windows95 machine or a non-Windows95 machine, or something of the sort.

Well, I've got one other hopeful choice to try this install on: a Gateway Essential, Celeron machine, also the same amount of ram (256megs) as this Micron Millenium, but having only an 8gig hard drive.  And it doesn't yet have an ethernet card.

I *do* have a 100gig hard drive still in the shrink-wrap that I got on sale a few weeks back and then wound up not using, but it seems like such overkill to use it for this purpose...

Anyone have any experience with either of these machines?

---

### Post by greenstar on 2005-09-26
Every time I've gotten a Grub loading error, it's been due to a bad burn. I learned about the value of checksumming .iso's and discs this way. Avoids coasters. Usually the culprit is a bad download, the checksum fails on the .iso, but occasionally I get a checksum fail from a disc when burned faster than 4x, but at 4x or slower, I've had no (zero) problems when burning checksummed images.

Try checking the md5sum of the .iso, then burning the install cd again at 4x or less, then check the md5sum of the disc and if all is ok, then try reinstalling.

Given that you have Breezy 5.10 preview install cd & your .iso is in /home/nomad then:
```
md5sum ubuntu-5.10-preview-install-i386.iso
```
should checksum the image, compare the result to the md5sum available at: [http://us.releases.ubuntu.com/releases/5.10/MD5SUMS](http://us.releases.ubuntu.com/releases/5.10/MD5SUMS) for Breezy 5.10 preview install the checksum is 88c0d18ee3dfee3fb2e2651c75044db3 for i386 architecture.
Then checksum your cd after burning:
```
md5sum /dev/hdx
``` where x=your cdrom drive with the breezy cd mounted. Compare this result to the appropriate checksum.

I know it probably sounds like a big hassle, but it's cheaper and less maddening than burning coasters.

Hope this helps,

greenstar

---

### Post by NomadOfNorad on 2005-09-27
Well, I've just checked the md5sum on the install CD iso, and it passed, so the problem isn't a corrupted CD image...

I'm not sure how to checksum the already-burned CD itself, though... so I haven't checked that one yet.  I'm checking and burning these ISOs on a peecee running Windoze, BTW.

---

### Post by greenstar on 2005-09-27
[QUOTE=greenstar]
Then checksum your cd after burning:
```
md5sum /dev/hdx
``` where x=your cdrom drive with the breezy cd mounted. Compare this result to the appropriate checksum.[/QUOTE]

greenstar

**edit:**

I just noticed what you said about burning & checking on windows. Try gnomebaker (general burning), graveman (read/write .iso's and discs)

```
sudo apt-get install graveman 
sudo apt-get install gnomebaker
```

---

### Post by NomadOfNorad on 2005-09-30
Okay, well... I did a few more attempts at a reinstall, switched to that 100gig hard drive (which turned out to be a 120 gig drive, actually) and installed onto that. Kept on getting the same hung boot. I even re-burned the ISO image to a fresh CD, at 4x, to rule out a corrupted burn. Still didn't work.

I gave up on the machine, put one of the drives into another machine (disconnected the existing drive and switched to that drive), and tried booting it there. Still hung at startup. I did another fresh install to there, and it worked. It booted correctly on the new machine.

The new machine, BTW, was an old Gateway G6-450, Pentium II.

I'm just wondering now... if I switch the drive back to the Micron Millenia, would it boot there?

---

### Post by codejunkie on 2005-09-30
[QUOTE=NomadOfNorad]Okay, well... I did a few more attempts at a reinstall, switched to that 100gig hard drive (which turned out to be a 120 gig drive, actually) and installed onto that. Kept on getting the same hung boot. I even re-burned the ISO image to a fresh CD, at 4x, to rule out a corrupted burn. Still didn't work.
I gave up on the machine, put one of the drives into another machine (disconnected the existing drive and switched to that drive), and tried booting it there. Still hung at startup. I did another fresh install to there, and it worked. It booted correctly on the new machine.
The new machine, BTW, was an old Gateway G6-450, Pentium II.
I'm just wondering now... if I switch the drive back to the Micron Millenia, would it boot there?[/QUOTE]
switching the drive back to the Micron most likely won't work because of different hardware but it never hurts to try, as for troubleshooting the grub error your getting check how your drive and cd/dvd-rom jumpers are setup cableselect, master, or slave make sure your harddrive is on it's own ide cable and your cd/dvd-rom is on it's own ide cable and set the jumper on both of them to master also set the bootorder in the bios to cdrom,floppy then harddrive this is usually the default setup for most systems. on some older systems like compaq and hp they had trouble recognizing anything but setting the drive jumpers to cableselect. first set the boot order in the bios to cdrom,floppy and harddrive and your cd-rom and harddrive to master  if that dosen't work just change the jumpers on your cd/dvd-rom and harddrive to cableselect let me know if that helps.

---

### Post by NomadOfNorad on 2005-10-01
The CD-ROM is on its own IDE channel, and the cable the hard drive is on has only one connector. I've had the hard drive jumpered for master and for cable-select, it didn't make any difference.

Haven't checked to see whether the CD-ROM drive was set to master or to cable select, though.

---

### Post by codejunkie on 2005-10-01
[QUOTE=NomadOfNorad]The CD-ROM is on its own IDE channel, and the cable the hard drive is on has only one connector. I've had the hard drive jumpered for master and for cable-select, it didn't make any difference.

Haven't checked to see whether the CD-ROM drive was set to master or to cable select, though.[/QUOTE]
what's the boot order in your bios set to?

---

