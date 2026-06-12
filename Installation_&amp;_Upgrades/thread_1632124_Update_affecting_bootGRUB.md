---
title: "Update affecting boot/GRUB?"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by Ubun00btu on 2010-11-27
I updated my current Ubuntu 64 bit installation which came with a GRUB update (I dual boot w/ win 7).  I did the installation and shut the computer off for the night.

The next day when I started the computer up I got a "ticking" noise from the PC speaker after the computer searched for installed SATA/IDE equipment at the POST.  It sounds just like a stuck key - like when you need to press F8 or DEL for boot options/BIOS and keep pressing it.  The ticking stops as soon as splash screen for either OS pops up, but the problem is that the startup blows right through the GRUB OS choices screen.  After the GRUB update it defaulted to the first thing in the menu which is the latest Ubuntu kernel, I had it set to #8 which is my Win 7 boot.  It's instantly selecting the highlighted OS, even though the timer is set to a 10 count. 

Thoughts?

---

### Post by drs305 on 2010-11-27
Here's my guess. If grub2 doesn't think there is a second OS on the system, it won't show the Grub menu. It's possible during the update it didn't see Windows and is reverting to it's default behavior.

Try holding down the SHIFT key during the initial boot and see if the Grub menu appears. It's also possible that the ESC key can call it up in certain circumstances.

If you get the menu, boot and then run "sudo update-grub". If Windows is found, the menu should reappear. You will have to reselect the proper default entry in /etc/default/grub. 

You may also want to place a # symbol at the start of the GRUB_HIDDEN_TIMEOUT line in /etc/default/grub. This will cause the menu to be displayed even on a single OS system.

If you still have problems, post the contents of RESULTS.txt by running the boot info script while booted to the LIVECD.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Ubun00btu on 2010-11-28
The thing is that the GRUB menu did show up with all the kernel/memtest/windows options, but it was for a split second and then the highlighted OS was selected instantly.  If I edited the grub config file to default highlight memtest, it would go to that instantly, the same for windows, etc... So it knew where to find and boot the other OS.  

I did the GRUB update command in terminal when I initially had the problem, it said everything was up to date and no files were changed.

Here's what fixed the issue:  I went into BIOS at boot and changed the boot order of HDDs.  I thought that seeing as the ticking didn't start until the HDDs were found by the system and the boot process began and the sound stopped as soon as an OS began to load that the problem pretty much resided with GRUB. It appears that the Ubuntu GRUB update decided to change where GRUB was installed.  Changing the boot order in BIOS solved the problem by putting the other HDD first.

No more ticking sound and the GRUB menu acts normally.

Very odd.

---

