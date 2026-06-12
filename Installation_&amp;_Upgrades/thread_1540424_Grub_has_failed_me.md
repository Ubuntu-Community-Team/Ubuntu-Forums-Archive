---
title: "Grub has failed me"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by ecujak on 2010-07-27
Whenever I load Ubuntu on a machine with other OS(s) loaded it always recognizes and adds an entry in the bootloader menu. Not this time. Well kind of. After the install my windows boot option was in the menu, but after an update it is no more. I see the different Linux images... but no Windows boot option. Can someone tell me how to add my windows XP boot option back to the bootloader? I have XP on the the on the 5th partition and Ubuntu on the 6th...

---

### Post by Cason on 2010-07-27
Have you reupdated GRUB after installing the update? If you haven't open a terminal then run this command:
```
sudo update-grub
```

If THAT doesn't work, could you copy the text from your grub.cfg file (filesystem/boot/grub) and post it here so we can see what your bootloader info looks like? Maybe that would give some clues as to the problem...

---

### Post by drs305 on 2010-07-27
Run "sudo update-grub". 

If that doesn't work, take a look at this link on restoring another OS after an install:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

If that doesn't help, please post the results of this script so we can see the status of your system:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
Place the results between "code" tags; generate the tags by pressing the # icon.

---

### Post by ecujak on 2010-07-27
yes I have ran ```
sudo update-grub
```

Thanks drs... I will try your links. I have been reading the grub2 manual but I think I am too impatient at this moment to understand.

---

