---
title: "Installing onto old laptop..."
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by owenwarner on 2005-04-07
Hey there,
   I recently pulled my old thinkpad 760xl out of the closet and decided to throw ubuntu onto it.  It'll boot cd's/floopys, but it won't boot the live cd or ubuntu cd is general.  After looking through documentation I realized I would need to boot with GRUB.

Now the laptop is a 2.1gb HDD and has windows 95 on it right now.  I could partition it I supposed, but how would I go about installing it?  Using GRUB command line and loading vmlinuz and the kernel?  I plan to format once getting into the installer, so how should I work this all out?  If it is possible I would just flash the bios if it would let me boot to CD, but it wants me to boot from floppy.  So, is there an ubuntu boot floppy, or boot floppys.  (which would most likely be 15 or so, like the debian floppy install)

So, ideas?

---

### Post by owenwarner on 2005-04-08
Ok, I tried to boot with smart disk manager boot loader.  Since I have to hot swap the drives it would not read the cd-rom when it was swapped.  Therefor getting 'Disk Error 0x80'.

---

### Post by az on 2005-04-08
If it will boot cds, why won't it boot the install cd?  What happens?

---

### Post by owenwarner on 2005-04-08
[QUOTE=azz]If it will boot cds, why won't it boot the install cd?  What happens?[/QUOTE]

The thing is, the only cd I've been able to get it to recognize/boot is the windows 95 disc it came with.  So unless I take that disc and rip apart the autoboot, I dont know if it'll boot cd's.

---

### Post by Grant on 2005-05-14
I would really like to know if you have made any progress with this.

My friend has a 760ed Thinkpad with an external floppy drive.  AFAIK it can't boot from CD, but I made a Smart BootManager floppy, which lets you boot a CD.

Thing is, it hangs really early in the install.  No error messages, doesn't respond to anything except power button.  It gets as far as detecting the hardware, goes to a blank screen and freezes.

---

### Post by hubuntu on 2005-05-20
Well... I did install debian woody on my old Thinkpad 760LD.. Using an odd trick though:

I started the PC with a Linux boot disk and once the kernel was loaded onto memory I switched the flopy drive with the CD drive, which then was recognized as a hd device and well the rest is history...

Tip: you *MUST* use under 9 seconds to do the switch.. good luck.

---

