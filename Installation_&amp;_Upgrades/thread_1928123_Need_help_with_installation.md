---
title: "Need help with installation"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by vuici.valentin on 2012-02-19
So, the deal is . . . i downloaded wubi, ran it from windows7 ultimate 64 bit (not that i think it matters), it ran perfectly, after restart it said something about resuming installation, and there i got a blank purple screen . . . for like 30 minutes. restarted, noticed that it said something about installation options if i pressed ... some key - don`t remember which right now - selected acpi workarounds. I did it, it installed, downloaded things and istalled them, then ... after restart, blank purple screen again. Needless to say i`m frustrated. The thing is that i don`t get that option with acpi workaround now. There is a menu when it boots ubuntu, but none of the work. PLEASE HELP. 
 
If it helps: my PC configuration is:
 
MB: Asrock P55PRO-USB3
RAM: 4+4 Gigs kingmax DDR3 1333MHz
Processor: i5 quad core
Video: Leadtek GTX560Ti
HDD1: 60 gb corsair ssd
HDD2: WD 640gb
HDD3: WD 1TB
HDD4: Samsung 320gb
2 DVDRW

---

### Post by MAFoElffen on 2012-02-19
> **vuici.valentin said:**
> So, the deal is . . . i downloaded wubi, ran it from windows7 ultimate 64 bit (not that i think it matters), it ran perfectly, after restart it said something about resuming installation, and there i got a blank purple screen . . . for like 30 minutes. restarted, noticed that it said something about installation options if i pressed ... some key - don`t remember which right now - selected acpi workarounds. I did it, it installed, downloaded things and istalled them, then ... after restart, blank purple screen again. Needless to say i`m frustrated. The thing is that i don`t get that option with acpi workaround now. There is a menu when it boots ubuntu, but none of the work. PLEASE HELP. 
 
If it helps: my PC configuration is:
 
MB: Asrock P55PRO-USB3
RAM: 4+4 Gigs kingmax DDR3 1333MHz
Processor: i5 quad core
Video: Leadtek GTX560Ti
HDD1: 60 gb corsair ssd
HDD2: WD 640gb
HDD3: WD 1TB
HDD4: Samsung 320gb
2 DVDRW
Okay then-
That video has a nVidia GeForce Fermi 114 chipset. If you had posted earlier, well... the acpi work arounds were probably not needed.

Next boot, use these instructions to use "nomodeset""
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

Then, after booting to the Desktop, go to System Settings > Additional Drivers and install your nvidia driver. (nvidia-current)

EDIT-- Sorry. Since you are using Wubi, go to the WUBI Megathread and look through posts 2-4. I think instructions for setting the boot options in Wubi are posted there. Use the same

---

