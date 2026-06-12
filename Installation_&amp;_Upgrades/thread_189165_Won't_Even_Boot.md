---
title: "Won't Even Boot"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Chiaro on 2006-06-04
I can't seem to get my motherboard to boot from the D: drive. I've tried SBM; it doesn't boot D: from there either.....


How can I get my computer to boot the CD?

---

### Post by adwait on 2006-06-04
Press del or delete or whatever to get into you bios setup (it will show which key to press when it is booting up, when its doing the momry test and stuff). Find the option for boot order in the bios setup and set it so that the CDROM comes before your hard disk.

---

### Post by Chiaro on 2006-06-04
The problem: CD is not in the boot order.

---

### Post by adwait on 2006-06-04
Ooh....ancient PC! try this
[http://en.opensuse.org/Install_on_PC_that_can't_boot_from_CD](http://en.opensuse.org/Install_on_PC_that_can't_boot_from_CD)

---

### Post by Chiaro on 2006-06-05
[QUOTE=adwait]Ooh....ancient PC! try this
[http://en.opensuse.org/Install_on_PC_that_can't_boot_from_CD](http://en.opensuse.org/Install_on_PC_that_can't_boot_from_CD)[/QUOTE]

> I've tried SBM; it doesn't boot D: from there either.....


Yeah....I believe I said I've tried Smart Boot Manager...

---

### Post by Nyati on 2006-06-05
I have been trying to get Ubuntu and Kubuntu to load from the alternate cd without an internet connection, so that I can upgrade from Breezy Badger, for 5 days now.

I'm not new to linux and I know all about sbm.

Quite honestly, I think this nix has taken a wrong turn and closed a door on thousands of potential users that may have helped erradicating BUG#1 - MS.

WHY produce a distro that requires a user to have a recent spec bios? The 2 IBM T30 laptops that I have been attempting this upgrade on, aren't that old, especially considering that they both have specs from production line release, that still kick the bytes out of new laptops today.

To add salt to the wound, my T30's don't have floppy drives.

How can the wizards behind this great distro forget about the folks that don't have all the requirements? The whole reason Linux is free and the principles behind the GPL and this new release, have been given a solid kick into the bin, a place usually reserved for MS.

WHY!!!!!

---

### Post by Chiaro on 2006-06-06
Um...sure...

Isn't there an option to install a boot entry that redirects to the CD? Like when I boot from C:, it lets me choose from XP or the Ubuntu CD?

---

### Post by Nyati on 2006-06-06
Chiaro

I've cracked it, and it may just be through our own expectation that things should work the way you expect them too, when they actually don't!

Firstly, how did you burn your alternate.iso cd?

This is what I did initially: 

I went into Nero burn, dragged the iso image from my directory folder into the cd burn folder and then selected burn --> set the ISO settings to ISO 9660:1999 and clicked burn <wrong turn>.

I then tried Nero Express and tried to burn a 'Bootable disc' which didn't do anything except load up Caldera Dos.

I then decided to use the menu's at the top of the Nero burn window (you know, the old fashioned way).

I opened up Nero burn, selected Recorder --> Burn Image..., chose the iso image I wanted to burn from my directory folder and then selected Burn on the top right of the window which opens up. I didn't change any settings, however I don't think this would make a difference.

Once in my IBM T30 laptop, with my Bios startup settings set to CDROM <pingpong> I have the bootable cd startup screen in front of me.

I hope this could solve your problem, if you've used Nero the way I have, thinking it will do things the way you expect, it won't.

Good Luck!

---

### Post by Chiaro on 2006-06-09
My problem is that I can't get my system to use the CD drive as a bootable medium....

---

### Post by confused57 on 2006-06-09
I realize you said you've tried SBM, but what does the SBM menu show when you boot up your computer with the floppy in the drive(booting first to the floppy?).  I'm just curious why SBM doesn't work with your system...I've used SBM successfully, I don't know what it may be  that SBM doesn't work for you.

---

### Post by Chiaro on 2006-06-17
It says
"Quit to BIOS
Shut Down
Reboot
Floppy
Hard Disk
Primary 1"

After clicking Floppy, it just blanks out then shows the same screen.

---

