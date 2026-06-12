---
title: "Help with partitions please (Boot Repair)"
date: 2022-04-13
forum: Installation &amp; Upgrades
---

### Post by ahmadmajid on 2022-04-13
Hello,

I was dual booting Windows 10 with Ubuntu, have been doing this with no issues for a long time. Today I decided I needed more space for linux, so I used disk management in Windows to make 10GB of unallocated space from the Windows 10 partition.

I then live booted via USB and used gparted to resize my Ubuntu partition up a bit. Now nothing boots on load.

I installed Boot Repair but wanted to check here first since this is the first time I've tried to fix something like this. I'll paste the bootinfo summary here: [https://paste.ubuntu.com/p/4hmCq2kz9b/](https://paste.ubuntu.com/p/4hmCq2kz9b/)

If I try automatic repair I get this: The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode.


I'm going to also search the forums but I wanted to post this too. Help highly appreciated :'(

---

### Post by ahmadmajid on 2022-04-13
As a follow up, I changed to legacy mode but now I can't even get to my boot manager to change this

---

### Post by grahammechanical on 2022-04-13
This was the instruction:

> The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode.  

You were supposed to use the UEFI settings to load the Ubuntu live session in UEFI mode in order to run the recommended repair offered by Boot Repair because both Windows and Ubuntu were installed in UEFI mode.

My guess is that you need to enter the UEFI settings utility by pressing ESC at the manufacturers splash screen. If you find yourself at a Grub command prompt then type exit and the machine will reboot.

Regards

---

### Post by oldfred on 2022-04-13
With UEFI system and UEFI installs, you must always boot in UEFI mode.
The setting in UEFI is normally for installed systems.

The UEFI boot menu should give two entries for booting Ubuntu live installer, one clearly UEFI like UEFI: xxxx and other just xxxx which is the BIOS boot. Some tools to create live installer may make it UEFI only or BIOS/CSM/Legacy only. Only choose UEFI if that is an option.

If you have UEFI fast boot on, you may not have time to press the key to get into UEFI settings or the key for UEFI boot menu. Fast boot assumes no system changes. Often a full cold boot, or total system shutdown will force a normal boot giving just enough time to press correct key.
If laptop you may need to remove laptop battery, so system is fully drained to do a cold boot not a warm reboot.

---

### Post by ahmadmajid on 2022-04-13
Hey,

I finally managed to boot into UEFI, ran the startup repair, looks like it worked. I'm going to restart my computer and then if it works I'm going to give you a huge thank you :') I've been so stressed about all of this. Just pasting the pastebin here after running startup repair so I don't lose it for future reference, then I'll also update this forum like you told me in the last comment.

[https://paste.ubuntu.com/p/j6JjK9Xdy2/](https://paste.ubuntu.com/p/j6JjK9Xdy2/)


Edit: Computer fully working again :) I'm content leaving that space unallocated for now, as today has been a scary day.

Big big thank you to the both of you. I literally couldn't have done it without either of you. The key I had to press to get into bios was delete by the way, which is a bit odd but it is what it is.

---

