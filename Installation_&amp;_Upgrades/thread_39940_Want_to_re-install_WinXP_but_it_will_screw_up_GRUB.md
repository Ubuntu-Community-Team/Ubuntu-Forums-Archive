---
title: "Want to re-install WinXP but it will screw up GRUB"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by dolny on 2005-06-07
Can I somehow re-install my WinXP? I'm running dual-boot system, with Linux as the main system, and WXP for some games. I know that re-installing XP (I have to do it, it works terribly) will destroy my GRUB. Is there any way I can avoid it?

---

### Post by tonym on 2005-06-07
Install GRUB onto the Linux boot partition rather than the master boot record.  When you have installed Windows use fdisk to make the Linux partition active.

---

### Post by El Cubano on 2005-06-07
Don't install GRUB to the Linux partition.  Simply install Windows XP and then when install finishes boot with your favorite live CD, mount your Linux partition and reinstall GRUB to the master boot record.  It is very simple.

---

### Post by dolny on 2005-06-07
Why isn't there a simplier method ;) ? I mean, in Mandrake (LILO) i just used 'rescue' command from the Installation CD and everything worked like a charm.

---

### Post by alainhenry on 2005-06-08
You could also have a GRUB floppy, or use a live linux CD, to run GRUB and issue the following commands:

root (hd0,4)
setup (hd0)

assuming Ubuntu root is on /dev/hda5.  See "Grub from the ground up" for more info
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

Alain

---

### Post by Dullin on 2005-06-10
The easiest way to do this is to boot up with the windows XP cd, go into the rescue console (choose repair un the boot menu of the XP CD) and then type fixmbr and voila all ready for our favorite redmond OS.

---

