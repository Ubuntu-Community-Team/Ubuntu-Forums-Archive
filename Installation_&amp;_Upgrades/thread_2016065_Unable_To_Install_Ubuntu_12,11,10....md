---
title: "Unable To Install Ubuntu 12,11,10..."
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by Bug Bladder Beast on 2012-07-04
I am new to the Linux world and have had limited exposure to Solaris in the past; way in the past.  As the title to this thread states I have been unsuccessful in getting Ubuntu 12.04 (i386, 64, and i386 alternate), 11, 10, Xubuntu 12.04, Fedora 17, and Debian to install on my home PC.


Windows     Windows 7 Ultimate Edition (64-bit) Service Pack 1 (Build 7601)
Internet Explorer     8.0.7601.17514
Memory (RAM)     6136 MB
CPU Info     Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
CPU Speed     2705.0 MHz
Sound Card     Speakers (Logitech G35 Headset) | Realtek Digital Output (Realtek | Realtek HDMI Output (Realtek Hi |
Display Adapters     ATI Radeon HD 5800 Series | ATI Radeon HD 5800 Series | ATI Radeon HD 5800 Series | RDPDD Chained DD | RDP Encoder Mirror Driver | RDP Reflector Display Driver
Monitors     2x; Generic PnP Monitor | ACER AL2216W |
Screen Resolution     1680 X 1050 - 32 bit
Network     Network Present
Network Adapters     Realtek PCIe GBE Family Controller #2 | Realtek PCIe GBE Family Controller
CD / DVD Drives     1x (F: | ) F: TSSTcorpCD/DVDW SH-S183L
Ports     COM Ports NOT Present. LPT Port NOT Present.
Mouse     16 Button Wheel Mouse Present
Hard Disks     C: 312.3GB | D: 182.9GB
Hard Disks - Free     C: 251.2GB | D: 77.0GB
USB Controllers     8 host controllers.
Firewire (1394)     Not Detected
Manufacturer *     Phoenix Technologies, LTD
Product Make *     OEM
AC Power Status     OnLine
BIOS Info     | |
Time Zone     US Mountain Standard Time
Battery Status     No Battery
Motherboard *     EVGA 132-BL-E758
IP Address     ***.***.***.*** |
MAC Address     **-**-**-**-**
Host Name     *****
SM BIOS     6.00 PG


     I have used both USB and CD media to attempt installation or running live and wind up with 1 of 4 results each time.  The most common is a kernel panic which can be seen in the attached photo.  The system will reboot after 30 seconds as promised.  The next most common situation during install is a black screen hang; nothing happens the computer screen goes black and it sits idle.  The third most common is a hang with text on the screen as it is going through the boot up process.  Finally the fourth most common is the Ubuntu load/splash screen hang.   The red dots are moving along just fine one minute and the next they just lie down and take a nap; no movement.  I have also tried changing some of the boot modifiers around to no avail.  

     Any help would be extremely, well, helpful.  Cheers! ):P

---

### Post by Quackers on 2012-07-04
Welcome to UF :-)
You could try one (or more) of the boot options listed in the thread below - I would suggest the nomodeset option at first and possibly the noacpi option later.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Bug Bladder Beast on 2012-07-04
> **Quackers said:**
> Welcome to UF :-)
You could try one (or more) of the boot options listed in the thread below - I would suggest the nomodeset option at first and possibly the noacpi option later.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


 Unfortunately I have used those already to no avail.  I called them boot modifiers in my original post rather than the more appropriate boot options.  Thank you for the reply. :p

---

### Post by Quackers on 2012-07-04
I see, did you try more than one at a time? Maybe nomodeset and noacpi or nomodeset and acpi=off.

---

### Post by sanderj on 2012-07-04
I would do two things:

1) from the cd/usb boot menu, select memtest86, and leave it running for a few hours. If it fails / gives error messages, the problem is somewhere in your hardware.

2) Google "machine check": processor context corrupt" ... it gives interesting information.

HTH

---

### Post by Bug Bladder Beast on 2012-07-04
> **sanderj said:**
> I would do two things:

1) from the cd/usb boot menu, select memtest86, and leave it running for a few hours. If it fails / gives error messages, the problem is somewhere in your hardware.

2) Google "machine check": processor context corrupt" ... it gives interesting information.

HTH


Ran the mem test for just under 2 hours with 0 errors.  I also google'd that error and was treated to a vague array of solutions; however it did lead to a solution.  I got to thinking about hardware issues, and as I am very hardware maintenance conscious (I dust regularly, replace thermal compund every year or so, re-seat memory and cards while I have the case open, and vacume out filters) it dawned on me that some setting in the bios might be the culprit, so I sifted through those setting.  I played with the HPET support, memory settings (making them low and slow), and even played with raid/AHCI configs all to no avail.  I finally just nuked the BIOS settings and put everything back into default.  Voila! Ubuntu went live!  I tried to break it again just to figure out what setting it was that kept me from installing but for the life of me I can't find it.  All my bios settings are back to how I had them and it goes live every time.  Needless to say I installed and everything seemed to go smoothly.  Unfortunately it is defaulting into Win 7 at boot so I need to figure out why it is not giving me the option between Ubuntu and Windows.  Consider the install issue solved, I guess.  

Thank you both for the info and your time. ):P

---

### Post by Quackers on 2012-07-04
Thanks for the update. That's good to hear.
It's not the first time a bios setting has interfered with things booting, but it's quite rare, in my experience.
Enjoy Ubuntu! :-)

---

