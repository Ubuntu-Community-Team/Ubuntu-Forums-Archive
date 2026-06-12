---
title: "Ubuntu 6.10 Desktop boot/video problems"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by xunil76 on 2006-11-28
i'm pretty fluent with Windows (since Win95), but mostly noob to Linux (although i have dabbled a little with a few other distros before Ubuntu...mostly SuSE 9.2 Pro, before the whole Novell/MS debacle).  but never really got too serious about it until i found out about the concept of "trusted computing", and the total bloatware piece of junk that they call Windows Vista).  i have used PC's for over 10 years and built many custom computers during that time, and have worked in the tech support/help desk field for over 7 years, so i'll try to include as much info as possible...let me know if you need anything more.  ;) 

===========================
The Systems:

System 1:
============
Viewsonic 2750w 27" widescreen LCD TV (connected via VGA cable)...1280x720 native resolution
AMD Athlon XP Mobile 2500+ @ 1.8Ghz
1GB G.Skill PC400 Dual-Channel Kit
ATI Radeon X800XL 256MB (AGP)
Abit NF7-S v2 Motherboard (nForce 2 chipset)
Sony 4x DVD Writer
10GB Seagate IDE HD
Enermax 460w PSU


System 2:
============
Mitsubishi DiamondPoint NX85 18.1" LCD (connected via DVI-D)...1280x1024 native resolution
AMD Opteron 165 Dual-Core CPU (2x 1.8Ghz)
2GB Mushkin PC400 Dual-Channel Kit
eVGA GeForce 7800GT 256MB (PCIe)
Asus A8N SLI Motherboard (nForce 4 SLI chipset)
NEC 16x DVD-DL Writer
NEC 12x DVD-Rom
74GB Western Digital Raptor SATA 10k RPM HD
500GB Western Digital SATA 7200 RPM HD
Enermax 620w PSU

===========================
The Problems:

1)
on System 1, i can boot from the 6.10 Desktop/LiveCD with no problems, and can complete the full installation from the "install Ubuntu" icon on the desktop...however, when i reboot from the hard drive after the installation completes successfully, it gets to the Ubuntu screen with the progress meter on it where the bar goes right/left/right/left, finally loads from left to right until it gets to 100%, then the screen goes dark like it is trying to load the next screen (the one where it shows what modules it's loading), but it never gets that far and just locks up.  This has happened exactly the same way at exactly the same point when using both the Desktop and Alternative versions of 6.10 when installed to the hard drive.  on the last screen before it freezes, i notice that the signal the TV is reporting via the on-screen menu is a 1280x1024 signal, rather than the 1280x720 native resolution of the TV.  i've determined the cause of the freezing to be videocard-related, as i have pulled the AGP card out and put in an old Voodoo 3 2000 PCI card, and it lets me boot from the hard drive to the desktop with no problems whatsoever, but it only allows a max resolution of 1024x768, and the video card is pretty ancient...only 16MB of VRAM. i know the ATI video card is good, as i had it in the system booting WinXP Pro from the same hard drive before the 6.10 installation with no problems at all.

2)
on System 2, i have tried both the i386 and AMD64 versions of the Desktop/LiveCD, and neither one will boot completely.  it gets to the point where it loads the brown background with the Ubuntu box in the center (the one where it shows the modules it's loading), but the Ubuntu box in the center has distorted graphics, and it won't boot past that point.  the graphics look like an interlaced video that has had half of the fields scrambled/shifted so that all the graphics don't line up on the screen properly.  i have not tried a different video card in this system because: a) i do not have another PCIe card available, and b) it would be too much hassle where this system is located and how it's positioned to start swapping parts out.  not to mention, this system is still my main system with WinXP Pro on it (working perfectly, i might add), so i don't want to go fooling around with it too much...i just wanted to try the Desktop/LiveCD version to see if it would run on this system or not, because once i learn Linux sufficiently to switch from Windows completely (and figure out how to get World of Warcraft to work on Linux to my liking), i will be running it on my main system as well.

===========================

the MD5 checksums have checked out on all 3 discs that i've burned (desktop & alternate for i386 and desktop for AMD64). i burned the CD's at 16x speed (vs. the 48x max speed).  i used Nero from within WinXP Pro to burn the images (using DAO, _not_ TAO or DAO/96).  Nero has an option that verifies that the data written to the disc matches the image on the hard drive, and all discs checked out fine.  i also ran the "check disc" option from the boot menu during bootup, and all discs check out there as well.  i'm in the process of downloading the i386 & AMD64 versions of 6.06 LTS -- mainly just to see if they will have the same problems or not -- but i'm not at home right now, and i would like to figure out how to solve the problem anyway, for the experience/learning opportunity...i generally learn better by doing, rather than reading.

===========================
The Questions:

1) how can i find out exactly what is causing each system to freeze?

2) on System 1, how can i get the ATI card to output a 1280x720 signal that is native to the LCD TV, instead of the 1280x1024 it's currently doing?



just keep in mind that i'm pretty noob to Linux and have very little experience/knowledge with *nix command line syntax

---

### Post by satcross on 2006-11-28
I am definitely no expert in Ubuntu, but I had a similar prob.
What happened with me was my monitor would turn off when it got to a certain point in start up.
The computer was still on, but I could not see.  It took about 5 goes to figure out that I could still go into the terminal using ctrl-alt-F1.  Using the command sudo dpkg-reconfigure xserver-xorg I could get Ubuntu to autodetect my video card and get the right settings.
Hope this helps

---

### Post by xunil76 on 2006-11-28
ok, i tried the AMD64 Desktop/LiveCD version of 6.06 on System 2, and it is freezing at the same spot during bootup.  however, i was able to do the ctrl+alt+F1 to get to the command line, but that only worked if i hit it *before* the Ubuntu box came up in the center with the distorted graphics.  if i wait and let it get to that point, no key commands will respond at all, the only thing that works at that point is the mouse cursor.  i have to reset the computer to get anything else at all to do anything.

---

### Post by xunil76 on 2006-11-29
anyone have any ideas/tips/pointers/golden bullets?

---

### Post by gnyoda on 2007-02-12
Alternate cd is a god send for the shitty out of the box amd ati support.

---

