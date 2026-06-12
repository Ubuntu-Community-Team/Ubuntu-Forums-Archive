---
title: "Installing freezes at kernel init."
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by saskboy on 2005-07-25
I have had no luck installing the last 2 releases of Ubuntu to my computer.  Both times the intall has failed early on, shortly after the boot options are entered; it stops responding after it says it's doing something like unpacking the kernel [I don't recall the exact spelling of the last message before the cursor just sits there].

I've tried other linux distributions, and some of them have trouble too, so I know it's a hardware issue, but my machine works fine in Windows XP, so I think it's due to an incompatible part or two.  Here are my parts off the top of my head, in case you have an idea which one(s) is causing this hanging.

Asus motherboard A7V8X , AMD 1800+ CPU
512MB RAM
DVD+- drive
3 IDE hard drives
on board sound, and NIC
ATI 8500DV Radeon AllInWonder TV
LCD 17" Daewoo monitor

Thank you for any suggestions, feel free to email me,
Saskboy

---

### Post by TSJason on 2005-07-26
Hello,

 Normally the Asus mobo's and AMD procs work lovely in linux. I am running an Asus A8V myself with an amd64 3400+.

 I would guess that it's either a bios setup problem or that ATI card. If I play with the overclocking settings in my bios it will act stupid but using the recommended settings works great (not sure if your board has something similar). Also, I've switched over to all geforce video cards because nvidia has such great driver support. IMHO ATI's is less than fantastic.

---

### Post by Tortured-x on 2005-07-26
[QUOTE=TSJason]Hello,

 Normally the Asus mobo's and AMD procs work lovely in linux. I am running an Asus A8V myself with an amd64 3400+.

 I would guess that it's either a bios setup problem or that ATI card. If I play with the overclocking settings in my bios it will act stupid but using the recommended settings works great (not sure if your board has something similar). Also, I've switched over to all geforce video cards because nvidia has such great driver support. IMHO ATI's is less than fantastic.[/QUOTE]
 i have the same problem.

hope all works out

---

### Post by saskboy on 2005-07-27
Thank you both for your input.  I think my computer sometimes complains that it's overclocked, although I've meant to put my settings at the proper level, and it's running at 1533MHz like it's supposed to be at.  So maybe my FSB or something is overclocked and that's causing the instability during install.  To rule that out, I'm going to look at installing another video card, since the All In Wonder TV won't work in Linux anyway I've heard.


If anyone has any other ideas, please add them.

Thanks again,
Saskboy

---

### Post by saskboy on 2006-06-04
I managed to enter a boot string last time to get the installation to stop locking up.
Now I don't remember that string, or it is no longer working, because I've tried the following:
noapic nolapic vga=771 debian-installer/framebuffer=false pci=noacpi
and nothing is working. Turrning off framebuffer shows me text instead of a graphical screen that freezes.

My hardware hasn't changed except for a new 160GB IDE drive.

The last line in the error message says:
4294669.993000 Kernel panic notsyncing VFS unable to mount fs ..... (8,1)

---

