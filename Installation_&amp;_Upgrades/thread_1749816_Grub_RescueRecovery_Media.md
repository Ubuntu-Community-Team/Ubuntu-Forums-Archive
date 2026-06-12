---
title: "Grub Rescue/Recovery Media"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by nvdkgm on 2011-05-04
Made error while installing Ubuntu. Corrupted HDD. Did clean install of Linux and ran it for many months. No issue.

Decided to use recovery discs to get Win XP back and it worked w/out problem. Computer restarted and hit Grub Rescue: unknown filesystem.

Question: What to do w/ Grub Rescue to get Windows to load?

I have attached a screenshot of GParted so you get an idea.

I tried "sudo apt-get install lilo" and "sudo lilo -M /dev/sda mbr" and upon restarting got weird partially defined screen.
When trying "lilo -u /dev/sda1" I got fatal can not open conf file.

---

### Post by nvdkgm on 2011-05-05
Could someone please help me. I know I can reinstall Ubuntu but that would defeat the purpose of getting back Windows. I need Windows for school compatibility.

---

### Post by kansasnoob on 2011-05-05
I think your Windows recovery ate Ubuntu :(

That screenshot only shows two partitions, Windows and the old linux-swap, no partition for the Ubuntu OS at all.

---

### Post by nvdkgm on 2011-05-05
I am aware of that. I intended to remove Ubuntu for the time being and try to get the Windows Loader and Windows XP back on board to get some stuff done before I would reinstall Ubuntu in the near future again.

The question is, given that I had Linux and the recovery cleaned the drive and put XP. What do I do with Grub to get at Windows.

I just thought of this. Could one of my options be to install 10.04 side by side with Windows and see if that works to get back Windows?

---

### Post by kansasnoob on 2011-05-05
Follow the "How to restore the Windows XP bootloader" instructions here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by nvdkgm on 2011-05-05
Had Ubuntu HDD and nothing else. Used Recovery CDs  and format entire drive to install back to factory. Let it hit Grub Rescue on restarting. With LiveUSB of Ubuntu I mounted factory XP and used i386 folder to make Installation CD, after making exec, which never had a copy of. Used that to fix boot and MBR. >fixboot >fixmbr >exit and then restarted.

Worked for me.

---

