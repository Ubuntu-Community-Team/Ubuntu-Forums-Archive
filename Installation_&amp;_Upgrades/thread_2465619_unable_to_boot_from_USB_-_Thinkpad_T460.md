---
title: "unable to boot from USB - Thinkpad T460"
date: 2021-08-06
forum: Installation &amp; Upgrades
---

### Post by nolby on 2021-08-06
Hi,
I've bought a Thinkpad T460 and I'm trying to install Ubuntu in dual boot.

But i cannot run a live via USB.

In BIOS I've setted "secure boot" disabled and "USB UEFI BIOS Support" enabled. But pressing F12 i cannot see my USB pen in booting option.

I've tested all USB port and I've also triyed to run my USB pen on an old "non UEFI" laptop and it worked.


Where is my mistake?

---

### Post by ubfan1 on 2021-08-06
How did you create the USB pen?  The ISO boots both UEFI and legacy, but some tools will create media that only boots one way.

---

### Post by tea for one on 2021-08-06
> **nolby said:**
> In BIOS I've setted "secure boot" disabled and "USB UEFI BIOS Support" enabled. But pressing F12 i cannot see my USB pen in booting option.

Sometimes, not really specific to any particular PC, you have to cycle in and out of the installed OS before the one-time boot menu is fully populated.

Plug in your USB and boot into the operating system.
Can you see the USB drive in the File manager/File Explorer?

---

### Post by garvinrick4 on 2021-08-07
And you do have in bios to boot usb first in order. If so make another if
wont boot.

---

### Post by mIk3_08 on 2021-08-07
If you are unable to boot to your created Ubuntu USB setup maybe you have
unsuccessfully created the set up into your USB. 
Here's some guides that can help you recreate your Ubuntu USB iso setup
and make sure you have downloaded your Ubuntu iso here;
[HTML]https://ubuntu.com/download/alternative-downloads[/HTML]
Link below will help you create and install using USB
Quick Installation Guide using USBStick
[HTML]https://help.ubuntu.com/community/Installation/FromUSBStickQuick[/HTML]
Guide on How Make a LiveDVD
[HTML]https://help.ubuntu.com/community/BurningIsoHowto[/HTML]
Quick Installation Guide iso2usb
[HTML]https://help.ubuntu.com/community/Installation/iso2usb[/HTML]
Quick Installation Guide within Windows - Installation/FromWindows
[HTML]https://help.ubuntu.com/community/In...on/FromWindows[/HTML]
Ubuntu Community Installation Guide - General Help
[HTML]https://help.ubuntu.com/community/Installation[/HTML]

---

### Post by nolby on 2021-08-07
Hi... USB pen was created using the simple tool present in Ubuntu (now  I'm using Ubuntu 20.04 on an old T520). This tool doesn't have any  possibility to coose UEFI or legacy.

If I plug the pen into new PC Windows notify me that I need to format the device for use it as a storage pen.

In  booting priority I canoot se USB... usually I not modify boot priority  but I press button that allow me to select a temporary booting device  different than usual.


@ mIk3_08 I will try to follow your link.

---

### Post by Impavidus on 2021-08-07
> **nolby said:**
> 
In BIOS I've setted "secure boot" disabled and "USB UEFI BIOS Support" enabled.
Your UEFI has two modes: UEFI mode, that is the modern way, and BIOS/legacy mode, which emulates the old way. If you dual boot, you really want both systems installed in the same mode. And if you dual boot Ubuntu with any Windows later than Windows 7, you really want that to be UEFI mode. You should be able to boot Ubuntu with secure boot enabled, but this may require some workarounds, depending on your hardware.

> **nolby said:**
> Hi... USB pen was created using the simple tool present in Ubuntu (now  I'm using Ubuntu 20.04 on an old T520). This tool doesn't have any  possibility to coose UEFI or legacy.
The simpler the tool, the more reliable it is. I haven't used this particular tool in a while. If it simply clones the .iso to the usb drive, it should work on both UEFI and legacy (but won't provide persistence).

I've got no experience with Thinkpads. Some computers need some UEFI updates or some security settings changed before booting from usb.

---

### Post by nolby on 2021-08-07
My UFI is settet for Legacy priority (it comes in this setting) and it mount Windows 10 Pro. Considering this oprtion would be more easy.

I will try some different settings but I'm not feeling safe continuin to modify BIOS settings.

Last chance is to replace SSD wit a virgin one. Old Thinkpad can mount 2 differend storage disk, the newest whitout CD/DVD cannot.

---

### Post by sudodus on 2021-08-07
I have an old IBM Thinkpad, an old and a fairly new Lenovo laptop and a Lenovo Thinkstation. All of these boot without problems from USB drives, that are cloned from Ubuntu iso files.

I think you used the Ubuntu Startup Disk Creator, and if you were using it in Ubuntu 16.04 LTS or a newer version of ubuntu, it is a reliable cloning tool.

Look at the screen at boot, and you will see a tip about which hotkey to tap repeatedly directly at boot in order to get into the UEFI/BIOS menu and/or into a temporary menu. Depending on the age of the computer, there are different UEFI/BIOS systems, and those keys may be different.

If I remember correctly, F12 brings me to a temporary menu in the newer Lenovos.

---

### Post by nolby on 2021-08-07
Yes sudodus, it's true but... it doesn't work.

Pressing F12 I don't see the USB device.

Problem is not open UFEFI... but ther is some particular setting that enable booting.

---

### Post by tea for one on 2021-08-07
Do you have these firmware settings:-

Startup > Boot Device List F12 Option > Enable/Disable (only available when supervisor enters set up)
Startup > Boot Order Lock > Enable/Disable 

Info found via Lenovo Bios Simulator website [https://download.lenovo.com/bsco/index.html](https://download.lenovo.com/bsco/index.html)

---

### Post by nolby on 2021-08-07
Solved:

I've restored BIOS default settings and make another time USB pen.

Same USB hardware, same .iso file but different software; this time I've used Rufus (specifying UEFI mode)... and it works!




   
thanks everyone for the advice.

---

### Post by tea for one on 2021-08-07
Good news

Please use the thread tools to mark as solved 

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

