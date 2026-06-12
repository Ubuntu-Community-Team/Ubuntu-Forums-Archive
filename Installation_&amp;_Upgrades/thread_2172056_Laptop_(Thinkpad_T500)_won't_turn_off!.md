---
title: "Laptop (Thinkpad T500) won't turn off!"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2013-09-03
Now here's a problem I've never had before - my Lenovo Thinkpad T500 won't turn off.  If I choose "Shutdown" from the menu, or enter "sudo shutdown -h now" at a console, the machine obligingly shuts down - then immediately reboots and starts again.  The only way I can get it to actually turn off is to remove the battery and then re-insert it.  This seems to break the reboot cycle.  But why is the laptop rebooting instread of shutting down, and how do I get it to behave properly?

---

### Post by tgalati4 on 2013-09-03
It could be damaged shutdown circuitry.  The machine powers off by switching very small transistors on the motherboard near the power jack and power circuitry.  Perhaps there is dirt or dust in that location.  Otherwise, you are looking at replacing the motherboard because repair is difficult.  You can try reflashing or upgrading the firmware.  Also, try booting from another CD/DVD with a Live Session and see if you can shutdown completely.  If not, then you can be reasonably sure that it is a hardware problem.

Unless you are dual-booting, you shouldn't have to turn your machine off very often.  On my T43p, I only reboot once every 3 to 6 months, using sleep mode instead.

How old is the machine?

Check your BIOS settings, though I don't remember laptops having it, but some desktops have a "Reboot after power loss".

---

### Post by AussieGuy on 2013-09-04
Thanks for that - I never thought it could be a hardware problem, but maybe it is... it's about 4 or 5 years old, I think.  It's been a fantastic workhorse, and the screen resolution (1680x1050: WSXGA+) has been perfect for me.  I suppose I could ditch it in favour of a newer machine...which means going through all the rigmarole of trying to find what machines now run linux best.  And I still like the engineering and keyboards of the Lenovo laptops more than any other.

---

### Post by tgalati4 on 2013-09-05
I agree, few machines have the build quality of thinkpads.  Your machine is due for a cleaning.  Look online for a video for disassembly.  It's difficult but not impossible.  Look for that power-on circuitry and check for leaky capacitors, any moisture stains, and resolder any joints near the power jack.  Workhorse machine implies that you use it everyday, so it's due for an overhaul.  Back up your data and do it yourself or find someone competent like a local computer vendor--since thinkpads are business machines, many shops have experienced repair folks.

Otherwise you will have to change your work habits to leave it in sleep mode and not reboot or dual boot.

This is a similar problem, but on a newer thinkpad:  [http://ubuntuforums.org/showthread.php?t=2172243](http://ubuntuforums.org/showthread.php?t=2172243)

---

