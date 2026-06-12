---
title: "Video Mode Not supported"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by tessem11 on 2012-08-23
I have recently built my own desktop and installer ubuntu with the setting nomodeset. I used nomodeset in grub to install drivers. Now when I try to boot after grub it says video mode not supported:-(

---

### Post by YannBuntu on 2012-08-23
Hello 
Please indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by tessem11 on 2012-08-24
Here it is ```
 http://paste.ubuntu.com/1164626
```

---

### Post by YannBuntu on 2012-08-27
Please try this:

1) run Boot-Repair
2) Click "Advanced options"
3) Go to the "GRUB options" tab
4) Tick the "Uncomment GRUB_GFXMODE" option
5) Click "Apply"
6) Indicate me the new URL that will appear
7) Reboot the PC and tell me what you observe

---

### Post by tessem11 on 2012-08-27
still video mode not supported.

---

### Post by YannBuntu on 2012-08-28
**2nd idea:**

1) run Boot-Repair
2) Click "Advanced options"
3) Go to the "GRUB options" tab
4) Click the "Edit GRUB configuration file" button, this will open a text file. Remove the "#" at the start of the "GRUB_TERMINAL=console" line, then save the file. Close the text editor.
5) Click "Apply"
6) Indicate me the new URL that will appear
7) Reboot the PC and tell me what you observe

**3rd idea** (if the 2nd idea fails):
create a /boot partition at the start of the disk: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by tessem11 on 2012-08-28
Hey I pushed the wrong button and reinstalled but now it works in nomodeset so what do you think i can do for drivers. That was the problem I think

---

### Post by YannBuntu on 2012-08-28
> **tessem11 said:**
> I pushed the wrong button and reinstalled

reinstalled Ubuntu, or just pushed the "Recommended Repair" button ?

> **tessem11 said:**
> but now it works in nomodeset so what do you think i can do for drivers. That was the problem I think

If you need "nomodeset", you should report the bug in Launchpad (via the "ubuntu-bug linux" command), so that there is a chance that your PC will be better supported next release.

---

### Post by tessem11 on 2012-08-28
Reinstall and i built the pc. When it said video mode not supported it looked like it was the screen was saying it if that makes sense. It is an old Samsung Sync Master 151v Monitor and i am wondering if it needs drivers. like for windows.

---

### Post by NongA_TongE on 2012-10-26
So I think I'm having the same problem - but I can't even get that far.... 
 I have a DELL XPS Desktop that was running ubuntu 10.04 (dual boot with windows) with an NVIDIA GEFORCE 7900 series graphics controller. I am trying to do a fresh install of 12.10 from a disk - with a full wipe of the drive, etc. 
I make it to various points in the install, and then the screen will flicker, and the monitor goes black with a message saying that it "can't display this resolution - optimum resolution is 1280 x 1024" I've tried  selecting nomodeset from the installer's menu, and got as far as selecting my userid and password and when I click continue, it will do it again.  I tried runing the mini installer from a usb drive last night - and it did the same thing loading the cli interface. Any suggestions?

---

