---
title: "Hangs on third bar of load screen"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by biloxibeachboy on 2008-02-13
New to Ubuntu and having problems after installing it (installation seemed to go fine) on load it hangs on the third bar of the load screen:

System manufacturer Compaqq Presario 061
System Type: x86 based PC
Processor x86 Family 15 Model 4 Stepping 1 GenuineIntel ~2933 Mhz
Bios: Phoenix Technologies, LTD 3.08, 5/9/2005
Bios Version 2.4
Physical Memory 1,024 MB
Display 1:  Intel(R) 82845/GL/GE/PE/GV graphics card (LCD Monitor)
Display 2:  Vision Tek Radeon X1300 Series 64MB RAM (HD Monitor)
Display 3:  Vision Tek Radeon X1300 Series Secondary (LCD Monitor)
CD 1: TSSTcorp CDW/DVD TS-H492A
CD 2: MAD DOG LS-DVDRW TSH652M
Sound:  Realtek AC'97 Audio
Network 1: Realtek RTL8139/810x Fast Ethernet
Network 2: Bluetooth Personal Area Network
Network 3: Linksys Wireless-G PCI Adapter
Fixed Disk:  NTFS 74.52 GB dirve
USB installed items:  HP PSC 1400 series, Keyboard, Mouse, Bluetooth radio.

I've never seen ubuntu in action and would really like to see what it can do since I won't be upgrading to Vista.  I'm looking for options other than M$ proprietary software.  Everything I've read says that this is the way to go but only if I can get it to load.

Any help would be appriciated.

Allen  :confused:

---

### Post by Partyboi2 on 2008-02-13
try booting without the splash, When you boot at the grub menu choose the kernel you are going to boot into and press "e" then highlight the kernel again and press "e" again, then change the word splash to nosplash then press enter and "b" to boot. This might tell you where its getting stuck

---

### Post by biloxibeachboy on 2008-02-13
see next post -------->

---

### Post by biloxibeachboy on 2008-02-13
> **Partyboi2 said:**
> try booting without the splash, When you boot at the grub menu choose the kernel you are going to boot into and press "e" then highlight the kernel again and press "e" again, then change the word splash to nosplash then press enter and "b" to boot. This might tell you where its getting stuck

OK I figured out how to do what you said and here are the results (I'm only posting the last 7 lines from the screen):

[  134.887361] [<c02f0661>] do_page_fault+0x2f1/0x5f0
[  134.887592] [<c02eeb34>] error_code+0x64/0x90
[  134.887801] [<c02f0370>] do_page_fault+0x0/0x5f0
[  134.888011] [<c02eeb4c>] error_code+0x7c/0x90
[  134.888218] [<c02eeb34>] error_code+0x64/0x90
[  134.888423] [<c02eeb34>] error_code+0x64/0x90
[  134.888648] =======================      <---- that is 23  equal signs if that makes a differance.

It locks up at this point.  Can someone please help me figure this one out?

---

