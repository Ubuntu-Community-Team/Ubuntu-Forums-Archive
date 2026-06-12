---
title: "New Installation from DVD ISO failing?"
date: 2021-10-19
forum: Installation &amp; Upgrades
---

### Post by jbartosh2 on 2021-10-19
I've tried both Ubuntu & Ubuntu Studio ISO's and get this issue.  Hard to believe a problem right from bare installation / booting from optical drive?  What can be done?  Others having this issue?  Have tried other installation modes (OEM install)
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289315&stc=1[/IMG]

---

### Post by ubfan1 on 2021-10-19
Lets start at the beginning: where did you get the ISO, did you hashcheck it, how did you create the DVD, did you media check it?

---

### Post by T6&amp;sfpER35% on 2021-10-20
> [COLOR=#000000]Others having this issue?[/COLOR]
iv'e done countless installs with DVD only (never uses USB) and never had a problem . I also never checksum the ISO ( i know , i'm bad) 
i use Xfburn to create ISO .and set boot sequence to DVD drive 1st,obviously.

---

### Post by GhX6GZMB on 2021-10-20
I wonder why an install is trying to start snap. Doesn't make sense to me.

---

### Post by jbartosh2 on 2021-10-20
Downloaded iso from official web-sites (tried Ubuntu & Studio both), burned with k3b - did not check (I never do either) never had an issue with anything like this before.  I have snap issues on the current installation I have too (but can't believe that could be related from a direct book to disk.  Nobody else having this issue?

---

### Post by GhX6GZMB on 2021-10-20
Exactly at which point do you get these errors?
Right after power on/BIOS boot?
After the blue pre-installation screen?
After the full install?

The first line on your screen shot is harmless, but the errors are strange. You say "bare install". Did this machine have Windows on it before or is it virgin?

---

### Post by jbartosh2 on 2021-10-23
I have a Ubuntu 20.04 install on there that has some snap issue that prevents upgrading as normal so I figured save time instead of mesing around fixing that I'd just do a fresh install.  The error happens fairly quickly after the dvd has booted before any gui installation screens.

---

### Post by T6&amp;sfpER35% on 2021-10-23
at installation when it ask do you want to do this or that (wipe everything and install fresh or something else etc. ) i can't remember the exact options , choose wipe and install.
did you do that?

---

### Post by GhX6GZMB on 2021-10-23
> **jbartosh2 said:**
> I have a Ubuntu 20.04 install on there that has some snap issue that prevents upgrading as normal so I figured save time instead of mesing around fixing that I'd just do a fresh install.  The error happens fairly quickly after the dvd has booted before any gui installation screens.

I seriously doubt that your DVD is actually booting. This more likely comes from your existing install.
Check your BIOS settings.
EDIT: just tried an installation DVD myself. After some seconds of takataka, a language selection screen appears. Now I'm on Lubuntu which has a different installer (Calamares), but there's no big difference to the Ubuntu installer. You're not booting from the DVD, but from your hard disk.

---

### Post by guiverc on 2021-10-23
I would validate the ISO for starters ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0))

An invalid ISO off by a single bit will take hours-weeks of wasted time, yet the validation takes seconds...  I think of it as very cheap insurance.

I'm writing hundreds of ISOs to media per annum, and in my experience the write of ISO is the most common failure (*though I'm thinking of USB media where I experience 5-8% failure**; thumb-drives being cheap media*).  If the media didn't validate itself - I'd not trust it.

Note: I've not used CD/DVD media in a long time... except for minor testing in the *groovy* [20.10] cycle.  All I recall was that it was super-slow and required *immense *patience.


If I couldn't boot media on one box; I'd test the media on another box (*or usually two*); if it fails to boot & validate successfully on any - it's bad media.  If it boots & validates on the other boxes then it's valid media & the issue is specific to the box you're trying to install on.

PS:  Is your drive functional?   I've rarely written DVD media these days; but I've had to replace 3 DVD writers the last 4 times I've needed to actually write something (*the drives are getting old & failures are common now; thankfully I've still got a pile of spare drives*).  This may not be your issue, but I'd check it out given experiences I've had last 18 months with CD/DVD drives


FYI:  @ml9104, you'll find the Snap Daemon starting on Lubuntu media too; all Ubuntu ISOs have it as it's on the Ubuntu base system that needs to be there. Lubuntu has no snaps; but the [*mandated*] infrastructure is present.  Ubiquity's replacement installer will be a *snap* (Lubuntu has no intention of switching from `calamares` though)

---

### Post by GhX6GZMB on 2021-10-23
> **guiverc said:**
> 
FYI:  @ml9104, you'll find the Snap Daemon starting on Lubuntu media too; all Ubuntu ISOs have it as it's on the Ubuntu base system that needs to be there. Lubuntu has no snaps; but the [*mandated*] infrastructure is present.  Ubiquity's replacement installer will be a *snap* (Lubuntu has no intention of switching from `calamares` though)

Interesting. I've never noticed snap during installation and I'm surprised that it would already pop up at boot time.

And thanks for the heads-up, making snap a mandatory feature would make me look elsewhere for a distro. I hate it.
I like the Calamares installer, it's nice to work with.

Concerning media: I've never had a DVD fail yet, but yes, it does take 3...4 minutes to live boot, but so do my USB-sticks. Probably because my interfaces are USB 2.1.
The reliability of the USB-sticks is IME way below the DVDs, several have failed. Too much cheap electronic junk out there.

Cheers.

---

### Post by TheFu on 2021-10-23
I don't have optical drives anymore, but I've been having issues getting my Ventoy flash drive to boot on a new Ryzen system built this week. I haven't gotten to the point of doing an install - need to update some NVMe firmware first, but I'm not doing something right.  I think it is related to UEFI vs Legacy.  I'm getting an error for trying to boot an FreeDOS -based ISO under a UEFI boot.  Ventoy [https://www.ventoy.net/](https://www.ventoy.net/) has a way to address that, but it isn't working.  I did create the flash drive with just that single ISO on it, but that didn't immediately boot in legacy mode either. I'm sleeping on the problem.  Right no, the older OS is running and all the services it provides are working - it isn't really a desktop, so the basic igpu is perfectly fine. Is is mainly an NFS, Calibre, mpd, with a few virtual machines (nextcloud, wallabag, an IRC bouncer) and Jellyfin/Plex media server accessed by other clients around the house.

The current OS doesn't use UEFI.  It also doesn't really support the new GPU, so this is a perfect time to do a fresh install and use UEFI.

So, I'd ask if you are 100% certain that Legacy or UEFI is required for this system and for the Ubuntu ISOs.  I think the normal Gnome3 Ubuntu ISO supports both UEFI and legacy boot, but I don't know about the other one you tried.  I ended up disallowing all UEFI in the BIOS settings everywhere I could find them to get the old OS to boot. Basically, I swapped the MB+CPU underneath everything else in the system - changed from a Pentium to a Ryzen5, then wanted the system to boot and work. The first boot on the new system took way to long to get working - so many BIOS settings.  Then magically, it all started working - and I honestly don't know which setting(s) made that possible.

I've had a number of home-burned DVDs fail over the decades.  Often, the bits just start disappearing after about 5 yrs.  For anything really important, I burn par2 parity files with the data/files.  At least then, I'll know that corruption happened.  A few times, those par2 files have provided sufficient information to recover data off a failing disc.  [https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2](https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2) explains how.

---

