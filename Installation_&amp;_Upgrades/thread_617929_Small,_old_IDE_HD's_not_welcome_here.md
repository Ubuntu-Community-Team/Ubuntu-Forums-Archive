---
title: "Small, old IDE HD's not welcome here?"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by ChrisBieda on 2007-11-19
I am trying to lowball all the components in a PIII-500 system (Gateway Essential 500), except RAM: That I maxed out at 384mb, as much as the mobo will recognize.

But using ANY of a series of old, small IDE drives results in a "hard drive not found" error, no matter whether I use the ooowee-GUI-good install from the Gutsy LiveCD (live user works fine, by the way) or the text-mode install from a Gutsy Xubuntu CD.

The drives are good, really.  They not only take FAT32 and NTFS formats from a Windows machine to which I cable them, but (and here's the REALLY disturbing part): OTHER Linuxes (say Mandriva 2007, or Fedora 7) find the drives fine!  (But I WANT to use Ubuntu, not one of the others.)

Yes, the drives are found by the BIOS during POST.

During the install, I am prompted to manually choose a driver, and as these are all Western Digitals, I took a stab in the dark and selected the WDC7000 driver.  No dice.  "Drive not found."

The drives are a Caviar 36400 (tried two different ones), WD75 (tried two there too) and a 102AA (I only tried one of these before coming here).

Any ideas other than going Fedora or Mandriva?

---

### Post by louieb on 2007-11-19
Never seen Ubuntu (or any other Linux) ask for a hard drive driver. Just out of curiosity do you have the System Rescue or GParted live CD. does GParted on either CD detect the drives? 

Have you used the Disk Drake partitioner? It can do things to the partition table that GParted and Ubuntu won't handle.  

I've run the Ubuntu Gutsy live CD on a P2-400 w 384MB ram. 
Is that the CD you have? If so what does ```
sudo fdisk -l
``` lowercase L display?

---

### Post by mellowd on 2007-11-19
My server is booting off an old IDE 20GB and works just fine

---

### Post by ChrisBieda on 2007-11-20
MellowD: Oddly enough, this same system ran Xubuntu 7.10 like a champ on a 20gb Quantum Fireball IDE drive.  I uncovered this small-drive hostility when I attempted to dial-back the size of the boot (and only) drive.  Perhaps there is a "double-secret" probationary lower limit to the size of a drive onto which Ubuntu may be installed that is, evidently, below 20gb, but above 10gb?

LouieB: Yes, I do have gPartEd 3.4-10beta.  And it partitions the Western 102AA nicely.  I have a variety of Gutsy CD's, including the LiveCD, the alternate installation CD, and the alternate installation Xubuntu CD.  This same problem occurs with each of them, leading me to conclude that the problem is deep in Ubuntu!  

I was also amused to read another thread, posted after mine: [http://ubuntuforums.org/showthread.php?t=618106](http://ubuntuforums.org/showthread.php?t=618106).  While not precisely the same issue, it has some worrisome similarity, namely that other name-brand distros will go where the Ubuntu installers cannot follow.

sudo fdisk -l reports the following after booting the LiveCD: ABSOLUTELY NOTHING.  Yup, as soon as I hit "Enter," Terminal returns the command prompt.

---

### Post by louieb on 2007-11-20
Sounds like one for [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")
:guitar:If it can be verified and duplicated, then I bet it will get fixed.

---

### Post by Bartender on 2007-11-20
This is a shot in the dark, but is there a BIOS revision available at Gateway website?

I've dinked around with a couple of old, tiny drives and Ubuntu didn't have a problem.  That was back a few distros, so can't say for sure with 7.10.

Do you have an 80-wire IDE cable?  If there's a 40-wire inside I'd try replacing with 80.

In BIOS, is HDD detection set to Auto?  I assume it is but had to ask

---

### Post by az on 2007-11-20
> **ChrisBieda said:**
> 

But using ANY of a series of old, small IDE drives results in a "hard drive not found" error, no matter whether I use the ooowee-GUI-good install from the Gutsy LiveCD (live user works fine, by the way) or the text-mode install from a Gutsy Xubuntu CD.

The drives are good, really.  They not only take FAT32 and NTFS formats from a Windows machine to which I cable them, but (and here's the REALLY disturbing part): OTHER Linuxes (say Mandriva 2007, or Fedora 7) find the drives fine!  (But I WANT to use Ubuntu, not one of the others.)

How small are the drives?  You need a little more than 2 Gigs of hard disk space.  I have installed 7.10 on a 2.2Gig disk and a number of other small-ish disks (3.2 gig and 6 Gig) without any issues.

> **ChrisBieda said:**
> 
Yes, the drives are found by the BIOS during POST.

During the install, I am prompted to manually choose a driver, and as these are all Western Digitals, I took a stab in the dark and selected the WDC7000 driver.  No dice.  "Drive not found."


What do you mean?  You shouldn't be prompted for any driver.  Are you using "expert" mode.  If so, don't.  Expert mode should be renamed "debug" mode and should never be used unless you want to debug something.

---

### Post by ChrisBieda on 2007-11-20
BarTender: Tried an 80-pin, just for fun.  No help.  Also, I double-checked the BIOS revision level.  It is the newest.

Az: Mine are bigger than yours!  (Couldn't resist.)  Seriously, they are 6, 7.5 and 10gb respectively, and they should be plenty big enough as you have proven.

The installation method I am using is Xubuntu (7.10) *text*.  I prefer to install in text (the so-called "alternative" series) to avoid any screwy video issues, like (case in point) the LiveCD which in 800x600 graphical mode is too big to fit the screen (the the Cancel and Forward butons are off-screen).

The error arrives during the hardware detection sequence.  As it appears, it does CD drives first, then network cards, then "disk drives."  "No disk was detected" it complains.  "If you know the name of the driver needed by your disk drive, you can select it from the list."  

I will add one more datum to this profile before slinking off to the Bug Hut (and a Fedora install on this machine):  During the installation sequence, before I am prompted to choose a language, I see

ata1: SRST failed (errno=-16)

or something like that flash by (if there's a way to force a debug installation mode, or stop on error. I'm all ears).  Clearly "ata1" is the hard drive (since "ata0" must be the CD-ROM).

I searched for this problem and found someone else with it too: Xubuntu again (though I have dismissed the interface as a contributing cause and believe he or she would get it with Kubuntu just as easily) and a **40gb** hard drive, notably though, **Western Digital**.  I see a common thread that just won't break, and it is WD!

Az: I will hazard a guess that none of your tiny drive installs are on WD's.

---

### Post by ChrisBieda on 2007-11-20
**(Embed sound of middle-aged man smacking his forehead here.)**

Of course it had to be user error.  For those of you playing the home version of our game, old WD's (at least these) have a jumper setting for "SINGLE DRIVE."  (This has since been replaced by the much more modern and chic, "CABLE SELECT.")

I have a tendency (okay, a flat-out habit) to store my unused drives jumpered for MASTER.  As long as they are at the end of the IDE drive cable, I never give this a thought.  (I'm old-school, too.  I rarely employ the CS option, preferring to humiliate one drive by calling it "slave" and unjustifiably favoring another by calling it "master.")

My thanks to all who have wasted their time on me.  I have learned at your knees to treat old equipment with ample suspicion and thinly-veiled contempt (kind of like how my kids look at me).

---

### Post by az on 2007-11-20
> **ChrisBieda said:**
> 

or something like that flash by (if there's a way to force a debug installation mode, or stop on error. I'm all ears).  Clearly "ata1" is the hard drive (since "ata0" must be the CD-ROM).

Az: I will hazard a guess that none of your tiny drive installs are on WD's.

I have never had any problems related to a specific brand of disk.  

Boot the alternate cd and look through the F1-F10 help texts.  Booting into expert mode will allow you to debug.  I am not in front of a computer with an alternate cd at the moment, so I can't give you any more detail...

---

### Post by LarryT54 on 2007-11-20
Does your computer by any chance use the Intel 82801EB/ER IDE interface chip?

I have the same problem, and I found a post saying that a bug had been discovered in the new Gutsy kernel where the IDE hard disk will not be detected using this chip.  Here is the post:

[http://ubuntuforums.org/showthread.php?t=586894](http://ubuntuforums.org/showthread.php?t=586894)

Hope maybe this helps ......

LarryT54

---

### Post by NJC on 2007-11-21
> **ChrisBieda said:**
> Perhaps there is a "double-secret" probationary lower limit to the size of a drive onto which Ubuntu may be installed that is, evidently, below 20gb, but above 10gb?

 
As a FWIW, I installed Ubuntu 6.06 on a Quantum Fireball 5.1gb drive. And I just finished installing Ubuntu 7.10 on a Quantum Fireball 6.4gb - no problems with either drives.
 
EDIT: OK - I see you've figured it out. Mark your post accordingly as [RESOLVED].

---

