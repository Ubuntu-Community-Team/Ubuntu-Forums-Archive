---
title: "Ubuntu Server 14.04 installation hangs after 'Scanning CD-ROM' dialog"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by simons.junk on 2014-04-24
Hi everyone,

First time caller, long time listener. I'm trying to install Ubuntu Server 14.04 on to a new computer build, and am running in to problems early on in the installation.

I've burned the installation ISO image on to a DVD, and am able to boot from it on the PC I want to install it to. I go through the first few questions regarding keyboard layout, then the dialog box saying 'Scanning CD-ROM' comes up briefly before reaching 100% and disappearing. Then I'm just left with the blank purple screen, with no action on the HDD or DVD.

I'm at a bit of a loss as to where to begin troubleshooting. I'm using the on board graphics card and have it connected with HDMI.

I don't think there's anything strange hardware wise: 

Gigabyte GA-78LMT-USB3 (rev 5.0)
AMD FX-6350 CPU
2 x 4GB Kingston HyperX Blu 1333MHz DDR3
Seagate ST1000DM003
LG GGC-H20L Bluray / HDDVD/ DVD drive

Does anyone have any thoughts?

---

### Post by simons.junk on 2014-04-24
I should add that when I boot in Rescue Mode, it goes past the 'Scanning CD-ROM' section quickly and through to the next section 'Additional Components' with no problems.

---

### Post by simons.junk on 2014-04-24
Weird. After letting it sit for about 15 minutes on the blank purple screen, it started working again, went through setting up the user, asked about encrypting the home directory, then went back to a blank purple screen. There were a few other occasions where it sat to think for 5 minutes or so, but installation finished ok. (eventually)

---

### Post by joep-groovytunes on 2014-04-29
I have exactly the same issue and it also resolved after about 15 minutes.

Asus p5n-e sli, Version: 1.XX
Intel c2d E6550
2x DIMM DDR2 667 MHz

---

### Post by risingfish on 2014-07-26
I know, old thread, but it still seems to be an issue, and users are still installing it. I burned the ISO to a USB drive and am getting the same behavior. I'm just letting it site now after reading this thread.

In my case the hardware, if it matters is an old Gigabyte GA-MA78GM-S2H with a Phenom 2 940 and 8GB of 800 MHz DDR2. Seems like a good box to setup a ZFS share on for storage. :)

---

### Post by D.Dadsgé on 2014-09-24
I'm having the same problem here. Lets start the waiting game then.

My hardware:
[COLOR=#000000][FONT=Arial]ASUS P5Q deluxe
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Intel Core2quad Q6600
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Corsair DDR2/1066 2*2GB Dominator
1 x Kingston SSD 60GB 500/525 KC300
3x Western Digital HDD 2TB WD20EFRX Red

[/FONT][/COLOR]

---

### Post by jaagup-irve on 2015-01-14
I think that I solved the problem (for my server at least). The ps command on the second console shows that while the machine is waiting, the computer is trying to mount /dev/fd0 -- meaning that it goes for the floppy for some reason. I disabled the floppy in BIOS and the delay went away. Someone with more time might want to file a bug here.

But this thread gave me hope that the problem is solvable so thanks for the 15 minutes of waiting :)

---

### Post by mickandlisa on 2015-01-16
Disabling the non-existent FDD in BIOS worked for me, thanks for the tip!

---

### Post by josh-gourneau on 2015-02-09
> **jaagup-irve said:**
> I think that I solved the problem (for my server at least). The ps command on the second console shows that while the machine is waiting, the computer is trying to mount /dev/fd0 -- meaning that it goes for the floppy for some reason. I disabled the floppy in BIOS and the delay went away. Someone with more time might want to file a bug here.

But this thread gave me hope that the problem is solvable so thanks for the 15 minutes of waiting :)

This worked for me too, thanks!

---

### Post by MAFoElffen on 2015-02-10
FYI Notes-- Almost forgotten by many... While in Ubiquity, you can pop out to a shell via <alt><F2>... Back into the installer via <alt><F1> or exit. I do this to diagnose, install a missing driver or such. If more of a problem, I'll boot a kernel with  "nosplash text --verbose debug drm.debug=0xe plymouth:debug" as a kernel boot option to see what is going on. The fd is common, but other hardware may also play a factor. 

It also used to be (in Server, Mini and alt) that <cntrl><alt><F1> and <cntrl><alt><F4>... one session was the installer, while the other was the system console messages.

---

### Post by Lee_Bhogal on 2015-03-16
Oh man I'm glad I found this thread

How annoying that it tries to mount a floppy drive that isn't there. 

Disabling in Floppy in BIOS did the trick.

---

### Post by ekeis98 on 2015-06-07
A short reply for anyone with the GIGABYTE mainboard GA-H61M-D2D3 (or some kind of) who doesn't want to waste senseless time:

My mainboard had NO connector for floppy drives. Hence it had NO setting for disabling floppy drives. Regardless the ubuntu installation routine alway tried to mount /dev/fd0. After timeout it continued till the routine remount /dev/fd0 again and again. I wasted two hours for nothing just waitung for the next 15 minutes to timeout.

So I stopped the installation, looked for a new BIOS to download and install and all of a sudden... it worked!!

Hope that helps.

Best regards
Oliver

---

