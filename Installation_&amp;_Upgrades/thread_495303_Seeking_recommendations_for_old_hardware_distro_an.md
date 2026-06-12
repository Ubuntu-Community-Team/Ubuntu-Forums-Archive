---
title: "Seeking recommendations for old hardware distro and methods"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Brian Smith on 2007-07-07
I'm a happy Ubuntu user for a couple of years now, and I love to follow the releases of new distributions and versions, and have installed Linux onto older systems for family members whose computer use I have to "support."  I find that it's easy to support free and open source gnu/*nix OSes these days since they work so well and offer more capabilities in some cases than the typical paid systems from Microsoft and Apple, at least for internet and office applications.  I love it.  Hereare some statistics of the latest project machine that I need some re-motivation for:

the most current (Dell) bios won't allow the use of anything other than FD or HD as a boot device
     this is still true when using Smart Boot Manager
     this is still true when using GRUB
it's a socket 5 ATX-ish motherboard sucessfully running (for years) a socket 7 pentium-200MMX processor
it's got 96MB of ram installed, which I can max out with parts I've got to 128MB.

my goals for the machine are to use it (indoors) in a mechanical shop-like environment, for quick mid-project internet reference referrals, possibly webmail checking, and for viewing windows-created reference materials and running some windows-created utilities.  It would also be a secondary computer for communications in the rare case that my normal machine breaks down.  Having to "support" it after possibly giving it (again) away to a family member is also likely.  Here is my plan so far:

Install a win95 system on the primary master IDE HD.
Use GRUB either on a floppy and/or on the MBR of the above drive.
Install a Linux system to boot by default on the primary slave IDE HD
Secondary master IDE position contains a (no-bootable through bios) CD-RW drive
Secondary slave position is open for either a shared storage drive or system utility/restore drive bootable through GRUB

The bios permits this thing to switch itself on at a certain time every day, so that it will begin to run before I need it in the shop area, which is convenient, and immaterial to this question!

Initially, I thought that Fluxbuntu Feisty was going to be the ticket for this machine.
Fluxbuntu Feisty seems a little stalled, and I hope that Fluxbuntu is released as a desktop package for Ubuntu sometime, but so far....not.

Via floppy and USB, I've installed Damn Small Linux on the secondary slave drive as an "emergency" system, and win95 on the primary master drive, and GRUB on a floppy to choose between them and to boot whatever else the bios can see...

I'm all set to install what I want to become the primarily used OS on the machine, but can't decide what to use and do now.  Here are the features that I hope for:

1) GUI, the command line is a friend, but not a significant other for me
2) Decently snappy but fully secure web browser such as Opera to be installable
3)  Gnome-like auto-mounting and visual presentation of usable storage devices I attach to USB ports
4) Resource usage monitors to help tolerate sluggish performance and discern lockups/things to avoid
5) Simple security updates and simple package installations like Ubuntu, though I probably don't have to install very much
6) A wonderful online support community such as this one

This post about low powered/low memory systems is great, but now 6 months out of date:
[http://ubuntuforums.org/showthread.php?t=320511](http://ubuntuforums.org/showthread.php?t=320511)

DamnSmallLinux, with its preinstalled Fluxbox and Conky and many options for booting it are
super super great.  Presently I've got it on both the "backup system" hard drive and a USB stick, both
bootable from the GRUB floppy, but I'm not restricted by the sizes of storage media, and while I love it,
it doesn't quite have all the features I'd like, nor do I think it would make a good replacement for an ailing
Windows-running box to give to an untrained family member.

I think that the Xubuntu-Desktop package is just too heavy for this machine.  Not the worst thing in the world, but just a bit too laggy.  Perhaps a stripped down XFCE system could be OK, but the automounting of devices and desktop display thereof, along with some panel recource monitors would, I suspect, just be too much.  I'm willing to be shown otherwise!  For my OldWorld G3/266 PPC, 384MB RAM, that is just about right.


I can't figure out how to boot live CDs from GRUB on this machine, though I have copied the Fluxbuntu LiveCD onto a hard drive and toyed with different boot options to try to get it to boot the kernel from the
hard drive and run from the CD.
AntiX 6.5 seems to look almost exactly what I'm thinking of, and keeps me in the Debian family, but before
I go further with this, I thought I'd ask the recommendations of people here.

What distribution(s) and demonstrations/installation procedures would people here recommend?

Thanks for your time and attention.

---

### Post by Pumalite on 2007-07-07
You could give zenwalk a try:

[http://www.zenwalk.org/](http://www.zenwalk.org/)

---

### Post by Tommy on 2007-07-16
> **Brian Smith said:**
> I think that the Xubuntu-Desktop package is just too heavy for this machine.  Not the worst thing in the world, but just a bit too laggy.  Perhaps a stripped down XFCE system could be OK, but the automounting of devices and desktop display thereof, along with some panel recource monitors would, I suspect, just be too much.  I'm willing to be shown otherwise!  For my OldWorld G3/266 PPC, 384MB RAM, that is just about right.


I can't figure out how to boot live CDs from GRUB on this machine, though I have copied the Fluxbuntu LiveCD onto a hard drive and toyed with different boot options to try to get it to boot the kernel from the
hard drive and run from the CD.


Unfortunately, "oldworld" Macs have special challenges -- enough to say you can't use a Live CD without booting another OS first. (Most oldworld folks use BootX, which you install in a classic MacOS partition. So you boot into Mac OS 7, 8, or 9, and have BootX load linux.) 

I have Ubuntu 6.06.1 (Dapper) on this Oldworld Powerbook G3 Series ("Wallstreet II" / "PDQ") (266 Mhz G3 processor).

Unfortunately, Dapper is a challenge to install on oldworld hardware -- much easier to start with any older Ubuntu version and upgrade. Dapper is the last version that (in my opinion) has more things that work than are broken. I haven't even been able to reliably boot Edgy or Feisty, so I'm sticking with Dapper still. 

It's possible Gutsy will be better because some of the hardware issues may be fixed in the kernel and packages by then. BUT I wouldn't count on it because there don't seem to be enough oldworld PPC folks to catch the bugs as the new things come out. Kindof a self-perpetuating spiral downhill, because those bugs are keeping new folks from coming onboard.

I'm trying to be "realistic" instead of "pessimistic" -- I have some hardware I would love to keep using with the newer software, so every few months I try again.

IMHO Kubuntu 6.06 runs fine on a 266 Mhz PPC, but Ubuntu's Nautilus is a bit "heavy" for it and Xubuntu is better than KDE as long as you don't use Thunar (the default file manager). But I will readily concede these are entirely subjective!

---

