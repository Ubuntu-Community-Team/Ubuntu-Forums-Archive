---
title: "Ubuntu Lucid Lynx with Windows 7"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by NaartjieDude on 2010-09-12
Hello there.
I am using Windows 7 now, and would like to dual boot it with Ubuntu Lucid Lynx. I have 2 hard drives, partitioned like this:

Drive 1 : Windows Drive 150GB (A)
Drive 2 : 50GB free space (B) and Other Stuff Drive 250GB (C)

I would like to install Ubuntu on B, but it may not overwrite anything on C or A. Also, I would like Windows to have boot control (EasyBCD) as opposed to GRUB.

Is there any guide that can help me with this, or any specific things I have to do with my setup?

Thanks, 
NaartjieDude

---

### Post by Frogs Hair on 2010-09-12
It is possible to move a Wubi installation to its own partition and retain the Windows boot loader , but I'm not sure about moving it to a different hdd. I found instructions to do what you want to do for XP but not for W7 and of course it was use at your own risk.

---

### Post by Computer Guru on 2010-09-12
Hi NaartjieDude,

The instructions for exactly what you're asking for can be found here:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

(Note: these don't involve Wubi)

---

### Post by NaartjieDude on 2010-09-13
Thanks alot, that seems to be just what I'm looking for. I don't have much time now, but I'll try it later today.

---

### Post by NaartjieDude on 2010-09-13
I seem to have gotten stuck on the step where you have to Install 7 Bootloader to MBR. I click "Write MBR", yet when I restart to my PC boots into Windows 7 without showing the bootloader screen. This is somewhat urgent.

EDIT: I am leaving for a week, and won't be able to use the internet or access my computer, so please reply, just don't expect an answer before around the 19th of September :)

---

### Post by Computer Guru on 2010-09-15
That means you didn't add a Linux entry to the boot menu with EasyBCD.

---

### Post by Mark Phelps on 2010-09-15
> **NaartjieDude said:**
> I seem to have gotten stuck on the step where you have to Install 7 Bootloader to MBR. I click "Write MBR", yet when I restart to my PC boots into Windows 7 without showing the bootloader screen. This is somewhat urgent.

EDIT: I am leaving for a week, and won't be able to use the internet or access my computer, so please reply, just don't expect an answer before around the 19th of September :)

If you want to have Ubuntu and Win7 on different drives, there is a LOT simpler solution that works -- I know because I use it myself:
1) Leave Win7 alone on its own physical drive
2) Disconnect the Win7 drive
3) Boot from the Ubuntu CD with only the other drive connected
4) Install Ubuntu to the connected drive, including GRUB
5) Reconnect the Win7 drive -- but continue to boot from the Ubuntu drive
6) Once into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB menu and add an entry for Win7.

When you reboot, you will get a GRUB menu with entries for Ubuntu and for Win7.

---

### Post by dmp2010 on 2010-09-17
I have done similar. I have two hard drives. The drive one has Win 7 and nothing else. I disconnected other drive during this installation.
 
The drive two has both Win 7 and Ubuntu 10.1. Same here. I disconnected the first drive during installation. I mainly use this dual boot drive with Ubuntu being default. It gives an option to boot to Ubuntu or Win7. 
 
When I want to use the drive one which has only Win7, I change the booting oder in my bios. So, drive one would boot instead of drive 2. This works for me now. 
 
I suppose I can update the Grub as Mark suggested, but I am afraid to do it. Would it work for me?

---

