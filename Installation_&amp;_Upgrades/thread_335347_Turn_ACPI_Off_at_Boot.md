---
title: "Turn ACPI Off at Boot"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by scoutsa on 2007-01-10
Hi Everyone
I'm a complete novice with Linux so go easy on me. I'm in the process of trying to install Ubuntu "Dapper Drake" on an older pc. I've burned the iso to a cd and booted. Then clicked on start or install ubuntu and ended up with a blank screen. The error related to being "unable to load system desciption table" and a bit of serching led to an ACPI problem. After adding acpi=off to the boot options available on the CD install (ie press F6) I managed to boot to a useable desktop and run the install to hard drive app. The hard drive is a single partition with only this OS installed. However I still can't boot from the hard drive as ACPI isn't being disabled. From what I can tell I need to turn ACPI off in the boot menu - menu.lst but this doesn't exist. How do I create it, what do I put in it to just boot and turn off acpi? All help greatly appreciated.
Thanks
Deb ](*,)

---

### Post by Magnes on 2007-01-10
/boot/grub/menu.lst - there should be the file.

in the line looking something like that:

kernel		/boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro noapic

you can add acpi=off

kernel		/boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro acpi=off noapic

Hope it will work. I can't test it.
At system start you can type "e" (as edit) in the grub menu and then edit the lines of menu.lst entry to test (it won't be saved!).

---

### Post by scoutsa on 2007-01-10
Hi
Thanks - I'd finally figured that bit out and it does work. Press "e" to edit - make the change and then hit "b" to boot. Now I'm trying to make this permanent but I don't seem to have sufficient permissions to edit the menu.lst file....

---

### Post by erothoff on 2007-01-22
Hi scoutsa,
  you have come to one of my biggest beefs with Linux. Not having the ability within the program to jump to superuser and finish what you want. You need to go to a terminal and type
sudo gedit /boot/grub/menu.lst
(on ubuntu)

sudo kate /boot/grub/menu.lst

(on Kubuntu)

and 

sudo mousepad /boot/grub/menu.lst

enter you password, and then you will have the permissions to change the file.

---

