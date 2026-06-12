---
title: "GRUB problem? Dual boot system, Vista hangs on boot"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by ph1 on 2008-06-13
So I'm not sure if Windows has broken itself (wouldn't be the first time) or if Linux has somehow sabotaged my poor Wintendo, but I'm hoping someone can point me to how to fix it through Linux, with which I'm infinitely more comfortable. (terminal ftw)

So when I boot my Dell computer, I get through the bios loading to the grub menu.  If I select Ubuntu 8.04, everything works fine--boots up like a charm.  So I don't think I have a hard disk problem, unless the defects are not located in the Ubuntu section, which is at the start of the disk.

However, when I select Windows Vista from the grub menu, the screen moves to the Windows boot (I get green scrolling bars with Microsoft's name below) and then it moves to a black screen, fans whirring, with no hard disk activity, and hangs there, completely unresponsive, until I do a manual shutdown.

Does anyone have a suggestion as to what the problem is?  Would it matter if the MBR was messed up?  Is there something I can do while in Linux?  Is it a problem with GRUB that I can fix by adding a simple line or two?  (I don't want to use the Windows utilities unless I have to because I prefer GRUB to the MBR.)  I think either automatic updates broke Windows, installing ntfs-3g did it, or I broke it by force-mounting Windows in Linux after it shut itself down randomly while I was sleeping and I was too lazy to boot back into Windows and shut it down cleanly.

Any suggestions are much appreciated.  Many thanks in advance.

---

### Post by Pumalite on 2008-06-13
Edit menu.lst:
gksudo gedit /boot/grub/menu.lst
Add:
title Windows
root  (hd0,0)
savedefault  
chainloader + 1

---

### Post by ph1 on 2008-06-13
Thanks for the swift reply.

Last I checked, that's exactly what my GRUB looked like--I'll check again, something could have been modified with all the 8.04 updates that keep coming.

---

### Post by Mark Phelps on 2008-06-13
Change "root" to "rootnoverify" -- that's what I have in my multi-boot menu.lst file and it's never failed me.

---

### Post by Pumalite on 2008-06-13
Post: sudo fdisk -lu

---

### Post by LeoSolaris on 2008-06-13
Grub seems to be a red herring here. Windows boots. Once you get out of grubs screen and the Windows logo comes up, grub is done. It's not doing anything, it's all Windows at that point.

My best bet would be the force mount after an unclean shut down. Windows are fragile, and I think you just threw a baseball through yours.

In a bad shutdown, windows sets itself up for a screen in the reboot process that let's you direct it to safe mode, last known good config, regular boot, and a few other lesser used choices. If you force mounted after a bad shut down, it it will get confused.

Stick your windows install CD in and boot off it. Select the repair utility, and there ya go, a new panel of glass for your old windows installation.

Leo

---

### Post by ph1 on 2008-06-13
Thanks, LeoSolaris.  I was hoping it was GRUB because that'd be easier for me to fix...but Windows being broken what I was afraid of, but what I expected.  I'll give it a go and see if I get any results that way.

grrrrr Windows...............

---

