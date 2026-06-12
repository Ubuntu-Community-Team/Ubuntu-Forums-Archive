---
title: "Installation-problem on Gateway Laptop w/ Win7"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by DeviantART on 2009-12-15
_**[U]Computer Specs_**[/U]**:**
Brand: Gatway Laptop Nv5435u
OS: Windows 7 :(

My problem is getting Ubuntu 9.10 to boot from the Install-CD (Boot-Disk/ISO), which was burned specifically so I could put the CD into my new computer & wipe-out the *pre-installed* Windows 7, which I never intended to use on that computer.

Here's the steps I took & the what I encountered as I tried to install Ubuntu 9.10 from the Install-CD:

I hit F11 until a screen appears that says the following:

"Edit Boot Options

Edit Windows boot options for: Windows 7

Path: n\Windows\system32\winload.exe

Partition: 3
Hard Disk: 9d309d3

[ /NOEXECUTE=OPTIN

ENTER=Submit  ESC=Cancel"

**How can I get that computer to recognize the Ubuntu 9.10 CD? I haven't set-up an account on that computer, since I'm trying to avoid using Windows 7, as much as possible. I just want to use Ubuntu 9.10 on that computer. :D**

---

### Post by aston4 on 2009-12-15
go into your bios options, set to boot from cdrom first, put ubuntu disk in drive, restart computer

---

### Post by DeviantART on 2009-12-15
Thanks! Please tell me what key I should be press, in order to make the computer boot from cdrom first?

I'm stuck with the screen that says:
"Edit Boot Options

Edit Windows boot options for: Windows 7

Path: n\Windows\system32\winload.exe

Partition: 3
Hard Disk: 9d309d3

[ /NOEXECUTE=OPTIN <--[B] _NOTE_: "/NOEXECUTE=OPTIN" is the only part of that dialog I'm allowed to edit. Should I restart my computer, instead of editing that part of the Windows 7 screen?


[/B] ENTER=Submit  ESC=Cancel"

---

### Post by hansdown on 2009-12-15
Hi DeviantART.

I think that model lets you press any key to boot from cd when it first starts up.

A good bet is the DEL key.

---

### Post by DeviantART on 2009-12-15
I appreciate your help, HansDown. I pressed "ESC" key to move on from the last Windows 7 dialog-screen I mentioned (above). Then the computer gave me the option to continue with Windows 7 or **Press F8**

I pressed F8. After that, I the "Advanced Boot Options" dialog-menu appeared. It says the following:

"Choose Advanced Options for: Windows 7
(Use the arrow keys to highlight your choice.)

Safe Mode
Safe Mode with Networking
Safe Mode with Command Prompt

Enable Boot Logging
Énable low-resolution video (640x480)
Last Known Good Configuration (advanced)
Directory Serviced Restore Mode
Debugging Mode
Disable automatic restart on system failure
Disable Driver Signature Enforcenent

Sart Windows Normally

Description: Creates ntbtlog.txt, which lists all drivers that load during startup, including the last file to load before a failure.

ENTER=Choose  ESC=Cancel"

**What should I select from that menu? I believe "Enable Boot Logging" is possibly what I need the computer to do, but I'm not sure if that would make it recognize the Install-CD I put in my Gateway Laptop's disk-drive.**

---

### Post by hansdown on 2009-12-15
Sorry if you've already done this, but you need to restart with the CD in the drive, then the first screen you see, will have "press any key to boot from CD", or similar.

It flashes by quickly.

---

### Post by presence1960 on 2009-12-15
Not to be a wise guy but refer to the documentation that came with the computer. it will tell you whick key to press to get into BIOS. If you look at the text when you boot you may see a message Press Fx to enter Setup.

---

