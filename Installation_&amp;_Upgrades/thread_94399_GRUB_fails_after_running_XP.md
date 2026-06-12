---
title: "GRUB fails after running XP"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by mvcmac on 2005-11-23
Just installed Ubuntu 5.1 on a Tecra A4 in the second partition of the HD.
XP Pro is on sda1. Initial boot of Linux and XP pro works, can see both OS's in the Grub selection at bootup. After starting XP and opening Firefox, then shut down XP -> Grub is broken! No more OS selection visible. The bootup keeps recycling it self. I can get back to XP after installing Ubuntu completely. It seems impossible to select the Grub install alone in the setup menu. Need to run trough the entire install menu to get Grub to overwrite the previous (corruped) boot sector. Maybe there is a way to set it back to XP boot solely, but that's not really desidered either. Don't know yet what in XP ruins the boot script? Did verify the options in Sophor Anti Virus, but no luck. So I'm looking for a faster way to recover the GRUB script, until I can figure out what in XP does the damage, instead of re-installing Ubuntu from scratch. Trouble is I didn't get a recovery CD for this XP, the IT guys kept it!
If this problem was posted before, please direct me to the thread. Thanks

---

### Post by towsonu2003 on 2005-12-03
try this: [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

It says:
-------
Q: How to restore GRUB menu after Windows installation?

   1. Read General Notes
   2. Read How to use Ubuntu Installation CD, to gain root user access? (boot:rescue)
   3.

      e.g. Assumed that /dev/hda is the location of /boot partition

   4.

      # grub-install /dev/hda

[edit] you could also install grub to floppy(/cd?) and boot from there so xp can't touch it but I donno how to do that... try searching for a grub howto in google :)

---

### Post by bwog on 2005-12-03
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

for  floppy use /dev/fd0

Towsonu is right imo, putting grub on floppy gives you a working system so that you can find out which windows prog is writing to the mbr.

After putting grub on floppy, you may have to restore the mbr with the windows CD in  rescue mode (fixmbr, etc).

---

