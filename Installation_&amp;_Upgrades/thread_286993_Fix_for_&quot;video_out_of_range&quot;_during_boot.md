---
title: "Fix for &quot;video out of range&quot; during boot"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by frankelr on 2006-10-28
If you are like many others, who lost startup messages and/or
the Splash screen during startup or shutdown after an Edgy upgrade or install,  Here is a partial "fix" which got me working and might ""fix the whole problem for others.

Seems to be a conflict between the capability of LCD monitors (mine is a Dell E773fp) and the specific Edgy Splash.  You can try my "fix" by activating (type esc)the GRUB editor when the Gub option screen appears. select the kernel line you wish to boot from and edit that line (type e). Add one of the following: vga=785 (640x480) or vga=788 (800x600) or vga=791 (1024x768). vga=785 and vga=788 both work for me, except the Splash is offset) and vga=791 still gives me "video mode not supported".

Also delete the "quiet" command; this will restore boot up and shut down messages.  After you get a satisfactory Edgy boot up and down; edit menu.lst in the /etc/grup/directory. After that you also need to perform a "sudo update-grub", this is claimed to "protect your changes from future kernel updates".  Be careful if you have multiple disks to edit the menu.lst file in /etc/grub of the hard disk you are booting from.

I'd appreciate any comments, improvemets on my kluge fix and an answer to what is really "broken" in Edgy.  But this should get many of you who have the same problem as myself working

Bob:)

---

