---
title: "Dual BtUp installation Ubuntu13.10-Win8 not wrkng in HP PvllnTS14z. Get dark screen"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by marort2 on 2014-02-03
[SIZE=2]I just got a new laptop (HP Pavillion TouchScreen 14z) with windows 8.1 in it. I want to dual boot and install Ubuntu 13.10.  However I keep getting a dark screen every time I try. I have tried to install from CD/DVD as well as USB flash drive but both ways get the same results.[/SIZE]
 

 [SIZE=2]Once I press 'F9' at boot up to start from CD/DVD or USB I am able to see the options for 'Try Ubuntu without installing' and/or 'Install Ubuntu' (I already tried both). Then, I see the ubuntu logo & hear the disc loading, spinning, and reading. And I see the 5 dots  (white changing to red & vice-versa). Then it flashes a screen with an script (?), then it becomes completely dark. The power button is lit, but nothing happens (just like if it was in sleep mode) & it does not respond. So, I end up holding the power button to turn off the machine.[/SIZE]
 

 [SIZE=2]Is there a solution for this problem?[/SIZE]

---

### Post by oldfred on 2014-02-06
Are you booting with BIOS mode or UEFI mode. Best to use UEFI mode if possible, but a few systems only boot in BIOS mode.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some need boot options for video.
Some also find that screen is just dark and using function key to increase brightness works.

What cpu? And what video or dual video?
 Looks like a AMD system? You may need the very newest kernel to have it work well.

 The AMD Radeon Performance Is Incredible On Linux 3.12
[http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1)

---

### Post by marort2 on 2014-02-23
Thanks for the info you provided OldFred,
 

 I was able to install Ubuntu 13.10 in pre-installed Windows 8.1 on my HP Pavillion successfully. First, within Win 8, I added a new volume (unallocated) using Disk Management. Then I rebooted with LiveCD (Press F9) and at the GNU GRUB (Try Ubuntu without installing... ). From this screen, I entered 'e' to edit and added 'nomodeset' and pressed 'F10'... Boom! No more dark screen. Installation went fine from this point.

Now I have new problem(s), but I will open a different thread for this.  
 

 *Only Windows 8 loads automatically. I can get to Ubuntu by pressing 'F9' to load 'Boot Manager'. Then select 'ubuntu (ST500L T012-1DG142)'. How can I make the change so I get both options 'Ubuntu and Windows' at boot up?*
 

 Thanks

---

