---
title: "ubuntu wont install problem with bios"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by dirtrider1 on 2010-02-21
Hello my sister just got a new hp pavilion dv6-2155dx laptop and I wanted to put Ubuntu 9.10 on it but after I get to install screen and hit enter the screen goes black and does nothing, Ive been doing some researching on hp's website and apparently the bios is not acpi compliant . I also tried booting  Ubuntu 9.04 and it seemed to work but said reg object of EC device broken bios suspected and Ive also tried other distros but there all a no go. Is there any known workaround for this HP's support is of course no help since they say they dont support linux.

---

### Post by darkod on 2010-02-21
Boot with the cd, highlight the Try Ubuntu option but don't hit Enter. Hit 'e' instead. That should allow you to edit the boot lines. At the end of the line starting with linux.... add acpi=off. Press Ctrl + X to boot.

If it boots OK into the live desktop with acpi=off, finish the installation and after that you can boot the hdd install the same way and once it's working, you can add the command to make it permanent so you don't have to edit the boot line every time.

All of this provided it's the acpi issue.

---

### Post by dirtrider1 on 2010-02-21
For some reason it still doesnt work i turned acpi off then tried to boot into try before install mode then right after I hit enter a little thing blinks in the corner then the screen goes black and the fans start spinning

---

### Post by darkod on 2010-02-21
Did you try Safe Graphics? Maybe it's the video driver. On the main cd menu hit F4 to get additional options.

---

### Post by dirtrider1 on 2010-02-21
Yeah I tried safe graphics too I wonder if anyone else with this laptop has successfully installed any linux distro.

---

### Post by viper250 on 2010-02-21
your computer has a sata drive in it 
you need to enter bios and set the hard drives mode to ide
then ubuntu will detect and load it

---

