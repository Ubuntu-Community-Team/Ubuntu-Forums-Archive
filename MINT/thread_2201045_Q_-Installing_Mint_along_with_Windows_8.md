---
title: "Q -Installing Mint along with Windows 8"
date: 2014-01-22
forum: MINT
---

### Post by ravisuncar on 2014-01-22
Yup, I know there are many threads regarding this but i think my case is kind of unique.

What I have:
-------------
1. OEM System recovery disc (Win 8) (I cannot partition or anything while using this disc, it will just install how the OEM use to install Windows)
2. Live USB with MInt

What I want:
--------------
1. Dual Boot

Situation:

1. I re installed Win 8 recently, I have turned off the secure boot and when i selected the boot option i got 2 option** ( boot from Disc (UEFI) or Boot from Disc)**. I selected boot from disc (hoping this will give me less problems). After that i tried to install Mint. When i tried booting from the pen drive, i again got the same 2 option (Boot from Pen drive (UEFI) or Boot from Pen drive).

This is where the problem started, If i selected boot from UEFI pen drive, mint is unable to see Windows at all. If i select the other option, it is able to see windows, install along side it and then will ask me to reboot to complete install. When i reboot, i dont see Mint at all. My system directly boots into Windows.

So, I want to know the way to make my laptop dual boot. **I have the OEM DVD and so ready to even install windows again from scratch.**

Hoping for a solution.

Thank!

---

### Post by oldfred on 2014-01-22
If Windows is UEFI, you need all installs to be UEFI. 
Or you purchase another copy of Windows and install in BIOS mode so you can have all installs in BIOS mode. Your current product key from Microsoft is in UEFI for re-install in UEFI mode and only works with vendor version.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ravisuncar on 2014-01-23
Thanks for the resposnce, It appears I have been installing Mint properly. But in boot sequence i get to see 2 options " OS Boot Manager" and Laptop "Hard disc". I thought both are same and was booting from the "OS Boot Manager". When i tried booting from the "Laptop Hard Disc". I could see Linux and Windows. Thanks for the Help.!

---

