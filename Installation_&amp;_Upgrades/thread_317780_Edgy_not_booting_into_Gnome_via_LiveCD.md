---
title: "Edgy not booting into Gnome via LiveCD?"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by mirzmaster on 2006-12-12
Hi all,

I'm having some trouble with a new installation of Edgy.  The PC exhibiting the problems is an AMD Athlon64 3200+, on Asus K8V Deluxe motherboard, with ATI 9600 video and 2 x 250GB drives on SATA.

An important note:  I am able to boot and install Dapper with no issue at all.

What I'm experiencing with Edgy is that the boot/install never makes it into Gnome.  The initial splash screen appears, loading appears to complete successfully, the CD reads for a bit more, and then nothing.  At this point I would expect to see Gnome loading, but instead the screen remains blank (there appears to be signal, but just a blank signal).  I'm not sure if the LiveCD is making it into Gnome or not.

_Additional notes:_
[LIST]
[*]Once the screen goes blank and drive activity stops, if I press the power button the CD starts reading again, and then the CD drive ejects.  Removing the LiveCD and pressing "Enter" does nothing.  I have to turn the PC off manually.
[*]I have tried the "acpi=off" boot parameter.  It causes a kernel panic during boot.
[*]I have also tried the "noapic" and "nolapic" parameters.  They have no effect.
[*]I have checked the CD for errors.  There are no errors.
[*]I used to see a similar issue with the Dapper LiveCD, but booting into safe video mode worked just fine.
[*]I've tried booting up Edgy with safe video mode, but that has no effect.  I get the blank screen.
[/LIST]

Any more ideas?  ](*,)

---

### Post by Crooksey on 2006-12-13
> I used to see a similar issue with the Dapper LiveCD, but booting into safe video mode worked just fine.

So why not use it?

---

### Post by ToeKing on 2006-12-13
Sounds like the same issue I'm having.

[http://ubuntuforums.org/showthread.php?p=1880784#post1880784](http://ubuntuforums.org/showthread.php?p=1880784#post1880784)

---

### Post by BenWhitey on 2006-12-13
I have the same problem here.  I have no clue why.  Sometimes it works though so I was able to install 6.10.  I want to say the install was text based, because there was no real GUI.  It was not commandline though.  Also, the loading screen for ubuntu with the bar that moves across was in black and white.

The livecd would not work for me.  When I tried to go into the instalation process to delete my ubuntu partitions and reinstall, I get errors like nopci or something.

My computer specs:
AMD64 3500 Newcastle
2x1024 OCZ Platinum DDR400 XTC
eVGA 7900GT SS (one signature series card, I got it from RMA)
DFI LanParty UT nF4 Ultra-D
1x200GB Western Digital 7200RPM
1x120GB Seagate 7200RPM
1x300GB Seagate 7200RPM SATA

---

### Post by ToeKing on 2006-12-13
Word on the street is that the black and white thing is just a bug with the x64 version.  That one has been reported and others have said that it installed fine other than that.  Its black and white for me as well, but the i386 version looks fine until the brown screen.

---

### Post by mirzmaster on 2006-12-13
> **Crooksey said:**
> So why not use it?

Why not use safe mode?  As mentioned, safe mode on Edgy doesn't work although it did with Dapper.

---

### Post by mirzmaster on 2006-12-13
**ToeKing** and **BenWhitly**:  The difference between the issue I'm seeing and the issue you both report is that my LiveCD shows no errors at all, nor anything else on the screen.

In my case, the screen remains black after the LiveCD load process has finished.  Gnome never appears.

---

### Post by mirzmaster on 2006-12-13
I have a suspicion as to what Edgy/Gnome is trying to do.

One detail I left out is that my system has a TV Tuner card installed, and I now believe that Edgy is trying to use the TV Tuner as the primary video display adapter, or something to that effect.

I just tried booting into Edgy again from the Live CD, and before the system stopped responding where it has been, the screen flashed a few times, twice showing video grain on a black display.  I've seen that type of grain before, and it comes from the TV Tuner.

I'll test this theory by pulling the TV Tuner.

***Edit:**  Pulling the TV tuner had no impact*  :(

---

### Post by ToeKing on 2006-12-14
mirzmaster: gnome never loaded for me either with the live cd, but the screen wasn't black.  I did get it working tonight, though.  I was desperate so I tried something that was mentioned here.  The 6.06 live cd did correctly boot when I selected safe graphics mode.  After that I got another error when I told it to automatically partition my drive during the install...  After another attempt I manually did the partition and lo-and-behold 6.06 installed correctly!  Woo, once it rebooted the system has been running flawlessly.  I could update to 6.10 with the update manager and I've since installed the nvidia drivers.  All seems to be good now, I'm thrilled this finally works.

Side note: I tried to install Fedora core 6 before I attemped the Ubuntu 6.06 safe mode.  I saw the same problem that I was getting with the Ubuntu install, but this time the screen was blue (if I recall, I only tried once).  It changed the resolution and then hung before loading any splash screen or menu bars.  It seems that if I ever figure out why this wouldn't install I could use that universally.

By the way, the it was the x64 version of 6.06 that ended up working for me.

---

### Post by markdone on 2006-12-14
I am having the same issues the the installation. After the black and white bar my monitors both go blank and say that the input is out of range.

Computer Details:
Athlon AMD 3500 x64
2GB Ram
Dual Geforce 7600 GT's 
Creative Xi-Fi Sound Card
TV Tuner

---

### Post by mirzmaster on 2006-12-15
For everyone's benefit:  I was not able to resolve the issue, but I was able to workaround.  I did this by installing 6.06 Dapper, and then upgrading to Edgy.

**markdone:**  If the monitor says out of range, then likely you're experiencing xorg.conf issues.  Try booting up in safe graphics mode.

---

