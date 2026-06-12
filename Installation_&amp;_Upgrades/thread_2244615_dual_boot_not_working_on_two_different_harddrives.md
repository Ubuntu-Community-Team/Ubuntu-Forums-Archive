---
title: "dual boot not working on two different harddrives"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by susan5 on 2014-09-17
I have dual booted Windows and Ubuntu many times already on one harddrive, but am having problem with two. I have a windows ssd drive and another hdd I used for storage. I have partitioned the HDD to now allow ubuntu to be installed. So I installed Ubuntu on the partition of the HDD but am encountering problems. When I start my computer I wait for about 5 minutes, then grub shows up with a menu to choose and OS. When I choose ubuntu it loads, but when I choose Windows 8.1 it is just a black screen. I have tried boot-repair automatic repair, but it did not help.

---

### Post by yancek on 2014-09-17
The boot-repair has an option which outputs some data about your drive/partitions, boot files, etc.  It would be useful if you posted that.  If you didn't do that you can run it again and not try to do any repair just get the information.  You are going to be dealing with EFI/GPT partitions with windows 8 which adds a layer of complexity to the older methods.

---

### Post by ubfan1 on 2014-09-17
Can you select Windows from the efi boot menu(started by some function key, varies by machine).  Bug 1091464(?) may prevent booting Windows form grub when secure boot is enabled.

---

### Post by susan5 on 2014-09-17
[http://paste.ubuntu.com/8368871/ ]("http://paste.ubuntu.com/8368871/") This is the file that boot-repair creates

---

### Post by oldfred on 2014-09-18
I would use Boot-Repair's advanced mode to install a Windows type boot loader to sda. Then you should be able to directly boot Windows from BIOS or one time boot key.
And then you only want grub installed to sdb, which if you set it as default in BIOS can choose either Windows or Ubuntu from grub menu.

You do have to make sure fastboot or always on hibernation is off in Windows 8 even if booting in BIOS Mode.
Do you have AHCI on in BIOS?

Is delay before grub menu comes up, or after grub menu appears?
I do not see anything specific that would make system slow. 
What brand/model system and what video card/chip is this? Some require special boot parameters.

---

