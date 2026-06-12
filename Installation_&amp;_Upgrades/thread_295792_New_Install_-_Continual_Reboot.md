---
title: "New Install - Continual Reboot"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by rickyjones on 2006-11-08
Hey guys,

I have an older PC here that I'm installing Ubuntu Server on for use as (you guessed it) a server. It's an AMD K6-400Mhz box w/ 512MB RAM. I can't find any non-standard hardware on it (picked it up for like $40 from a friend.)

Ubuntu installs fine. However, when it reboots after the install, it goes through the POST, I see the grub loading screen, it says now loading (beginning to launch Ubuntu, not sure on the exact message, but it's a small sentence at the top left of the screen). Then it reboots. I've tried a new harddrive. I've tried running memtest86. I've reinstalled 3 times. I removed all other cards besides the NIC and VGA (3DFX Voodoo 3 AGP)... I'm running out of ideas.

I get no error messages and I'm unsure as to where to look next. Any ideas?

I appreciate the help!

-Richard

---

### Post by matt8534 on 2006-11-09
I am getting the same problem with a very similar machine, (500Mhz AMD k6 w/ 256MB RAM)  I also have reinstalled several times as well as ran memtest with no errors.  After the grub menu countdown ends I get a "starting up" that flashes at the top of the screen for 1/2 a second and then the machine reboots.

---

### Post by rickyjones on 2006-11-09
Anyone think that this might be a hardware issue or a grub issue? I'm getting a little frustrated over this.

To the more advanced users: would I have luck going in with a live cd and checking out the /var/log directory for anything? If so, what should I look for?

Thanks!

---

### Post by codejunkie on 2006-11-09
try booting up the machine with the ```
linux acpi=off
``` boot parameter

---

### Post by confused57 on 2006-11-09
It's a known bug with the Server edition iso on some older hardware:
[http://www.ubuntuforums.org/showthread.php?t=232685](http://www.ubuntuforums.org/showthread.php?t=232685)

Haven't tried codejunkie's suggestion...if it doesn't work, you could install a server using the alternate cd.

---

### Post by rickyjones on 2006-11-09
I will try the alternative install CD when I get the chance. I'll update if it still fails.

Thanks for the ideas!

-Richard

---

