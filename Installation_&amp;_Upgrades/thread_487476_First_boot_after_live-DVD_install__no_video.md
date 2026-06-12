---
title: "First boot after live-DVD install | no video"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by only_17_hours on 2007-06-29
Hello--

I have installed the 64-bit version of Ubuntu 7.04.  As a preface, when I booted from the live-DVD to get to the installer if I let the bootloader use the default entry as soon as the kernel would start to load I would get "blank" screen (no text on screen, but I could hear/see the DVD loading the OS).  At the bootloader screen if I changed the display setting to force 1280x1024 (32) I would see the boot splash screen(s) and be able to run the installer with no problem.

BUT, after installing and booting up for the first time the same issue happens, GRUB comes up and defaults to booting my new 7.04 installation, but as soon as that screen goes away and OS starts to load I get the same thing, a blank screen.  During this phase I can hear my hard drives working, so the OS is loading, but with no video it's rather pointless.

I have a new(ish) video card, an nVidia GeForce 8800 GTS.  I do not see it on the "supported hardware" list, but I would think I could at least get video of some kind.

BTW, I can use the failsafe kernel entry in GRUB and I get video with no problem, in all its standard VGA glory.  After that kernel loads I'm dumped to a command prompt where I am sure I could many things, but as I'm Windows dude I'm not really sure what to do.

(1) Could I edit the GRUB entry line to tell the kernel (or whatever) to force a certain resolution so I can see my display?  If so, I know how to edit GRUB entry, but have NO CLUE what to add to the entry?

(2) Is there some "config" file I can edit by using the failsafe kernel option that would allow me to then use the normal kernel?  I'm pretty new to to this so I would need to know the EXACT location of the file to edit and the name of a text editor that I can run from a command line.

If it matters:
Monitor is Samsung SyncMaster 226B (native resolution is 1680x1050)
I am dual-booting WinXP/64, which is working fine
Asus P5B-Deluxe Wi-Fi mobo, 4Gb RAM, Core 2 Duo 6600

I have searched through the forums, I haven't seen this exact problem, but if it's been asked before I apologise.  If more system information is needed, I can supply it.

Thanks for any direction and help in advance.

---

