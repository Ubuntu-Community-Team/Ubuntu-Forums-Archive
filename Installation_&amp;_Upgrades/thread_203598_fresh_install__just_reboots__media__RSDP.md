---
title: "fresh install | just reboots | /media | RSDP"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by kaze on 2006-06-25
Compaq Presario 1255
Machine had W9x on it
Machine had Ubuntu 5.x on it

Get a warning "*ACPI: Unable to locate RSDP*" early in the install
All power management off in BIOS

Went thru the install 4+ times already!

Instead of /boot and /, the installer sets the mount points as /media – what is this?
So after a failed install when I go back through the install and choose to manually partition I see this from the last go ‘round:
[FONT="Courier New"]#1 primary  49.3 MB B K ext3 /media/hda1
#2 primary   9.5 GB   K ext3 /media/hda2
#3 primary 501.7 MB   F swap swap[/FONT]

**Once the install is done and I reboot, it loads grub, then goes to boot. Instead of the OS coming up, it just reboots. Over and over.**

Had a 4 GB hard drive and when manually partitioning got errors formatting /, changed out to a 10 GB drive and got past that. Still exact same reboot issue though.

I checked the CD and it passes the tests

What to do? ](*,) 
- kaze

---

### Post by sickdude on 2006-06-25
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=301711](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=301711)

"Try adding acpi=off to the kernel boot parameters and see if it boots OK."

this is what i found when i googled your problem, maybe it will help you with your problem

---

### Post by kaze on 2006-06-25
**Thanks!**, but either I did it wrong or it made no difference...

Hit ESC to enter GRUB menu
"e" to edit the line
selected the kernel line
"e" to edit
changed from
[FONT="Courier New"]kernel /vmlinuz-2.6.15-23-server root=/dec/hda2 ro quiet splash[/FONT]
to
[FONT="Courier New"]kernel /vmlinuz-2.6.15-23-server acpi=off root=/dec/hda2 ro quiet splash[/FONT]
"enter" to save
"b" to boot
**same result**

[SIZE="1"](Note that the on screen instruction within GRUB are sub-optimal - you have to hit enter to save the changes, only option listed is esc, and you have to hit "b" to use your changes, anything else ignores them...)[/SIZE]

Thanks though...
- kaze

---

### Post by kaze on 2006-06-26
From this thread looks like an issue with the .iso...

[installation] Ubuntu 6.06 - Drake RC stuck in reboot cycle 
[http://www.ubuntuforums.org/showthread.php?t=185196]("http://www.ubuntuforums.org/showthread.php?t=185196")

Burning the alt iso right now...

- kaze

---

