---
title: "Dual Booting Problems"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by Circuit_tsunami on 2008-10-18
Hey... I'm a totally beginner and i have installed Linux on my first Hard drive and Vista on second. When ever I get to my grub I get the normal Linux and another Ubuntu that doesn't exist

(from memory)
Ubuntu 32bit blah blah
Ubuntu (memtest)
Ubuntu (fail-safe)
**Other Operating sytems**
Ubuntu 32bit blah blah
Ubuntu (memtest)
Ubuntu (fail-safe)

Now every time I want to boot into my Windows partition I have to change my integrated peripherals from Asci (that may be wrong doing all this from memory) to IDE or Raid and than change my hard drive priority. 

Any advice how to get it to work so that i can boot into windows from my Grub

---

### Post by Herman on 2008-10-18
:) Hello Circuit_tsunami,
To give you the help you need, someone will need to see a copy of the output from the 'sudo fdisk -lu' command, so if you can copy that and paste it into your next post please, that will help.

If you can boot Ubuntu and open a terminal (go 'Applications'-->'Accessories'-->'Terminal', and enter the following commands please,
```
sudo fdisk -lu
```
Also, anyone wanting to help will need to see a copy of the bottom part of your /boot/grub/menu.lst file, below where it says '## ## End Default Options ##', (where the boot stanzas are).
```
gksudo gedit /boot/grub/menu.lst
```

If you can get that information and post it here it will be a big help, thanks.

Regards, Herman :)

---

