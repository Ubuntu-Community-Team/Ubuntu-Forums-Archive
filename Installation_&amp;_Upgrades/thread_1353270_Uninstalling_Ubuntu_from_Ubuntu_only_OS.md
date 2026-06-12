---
title: "Uninstalling Ubuntu from Ubuntu only OS"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by blondibee on 2009-12-12
Hi, I installed Ubuntu 9.04 on my daughter's computer and it was working fine until I upgraded to 9.10.  Well anyways I am not computer savvy AT ALL and I would just like to uninstall Ubuntu completely and reinstall Windows XP because it is just easier for my 9 year old and me too.   I only have Ubuntu installed on her Dell desktop, not both Windows XP and Ubuntu like so many people have and read that all I need to do in put the Windows xp disk in and it will do the rest for me.  Well the problem is that when I go to change the boot order for the computer to boot from the CD drive the computer freezes every time and it will only boot from the hard drive.  I can't even enter setup without it freezing.  If anyone can tell me how to do this in the simplest way possible I would greatly appreciate it.  I don't know all the lingo so laymans terms would be great.   thank you!

:-k

---

### Post by darkod on 2009-12-12
You have to solve the problem with booting from the cd. You need that to boot with XP install cd.
After you've done that, in the screen where it asks you on which partition to install, you will have option to delete one by one all existing partitions, then create one or more new NTFS partitions for XP and that's it.
Are you sure you need to go into BIOS at all? Most computers would boot from cd first as default. Try boting with the cd without going into BIOS to see if it works.

---

### Post by Dennis N on 2009-12-12
> **blondibee said:**
> ...Well the problem is that when I go to change the boot order for the computer to boot from the CD drive the computer freezes every time and it will only boot from the hard drive.  I can't even enter setup without it freezing...
:-k

Just to clarify, how are you changing the boot order? Using F12, or trying to change in the BIOS settings?

---

### Post by blondibee on 2009-12-12
I hit F12 and it brings me to the boot order but the computer doesn't allow me to select the drive I want to boot from because at that point it just freezes which is why I can't boot from the xp cd.

---

### Post by dolo724 on 2009-12-12
On some older Dell computers (even for WinXP) a ps/2 keyboard is required to access the BIOS and boot-order settings. A USB keyboard will not work unless the BIOS is already set on these machines to recognize USB hardware.

You can tell which you have by looking at the plug on the keyboard cable:

ps/2 (mini-din) is round with pins inside 

USB is flat and rectangular

If you only have a USB keyboard, borrow or buy one and then try the same process. There should be a socket for the ps/2 plug on the back of the Dell. While you are in BIOS be sure to enable USB hardware.

After reinstalling Windows, which is time and attention consuming, you might be interested in keeping the Ubuntu Live disk to try occasionally. If it's Gnome you are having trouble with, try the Kubuntu instead, it's much more like Windows. (for similarity to WinXP, download the 8.04 version of Kubuntu)

---

### Post by presence1960 on 2009-12-12
> **blondibee said:**
> Hi, I installed Ubuntu 9.04 on my daughter's computer and it was working fine until I upgraded to 9.10.  Well anyways I am not computer savvy AT ALL and I would just like to uninstall Ubuntu completely and reinstall Windows XP because it is just easier for my 9 year old and me too.   I only have Ubuntu installed on her Dell desktop, not both Windows XP and Ubuntu like so many people have and read that all I need to do in put the Windows xp disk in and it will do the rest for me.  Well the problem is that when I go to change the boot order for the computer to boot from the CD drive the computer freezes every time and it will only boot from the hard drive.  I can't even enter setup without it freezing.  If anyone can tell me how to do this in the simplest way possible I would greatly appreciate it.  I don't know all the lingo so laymans terms would be great.   thank you!

:-k

Try hitting F12 ( I think that is what Dell uses) to get the boot menu when booting the windows install disk. Choose CD/DVD drive. This is a temporary onetime only boot order change. You will not go into BIOS this way. If F12 is not the key refer to your computer documentation or find the manual for your model on dell.com

---

### Post by blondibee on 2009-12-13
Thanks everyone for the help.   I think dolo 724 has maybe hit on something.  The keyboard on the computer doesn't have a usb plug but it does say keyboard failure during startup.  The funny thing is that when the computer boots up the keyboard works fine.  I do have a usb mouse on the computer but don't know if that could be a problem.  Any thoughts?

---

### Post by Mark Phelps on 2009-12-13
On some older machines, the USB ports aren't activated until you boot into Windows itself. If that's the case with your machine, you may need PS/2 plug versions of both a mouse and a keyboard -- although, BIOS settings normally don't use a mouse at all for selecting menu items.

---

### Post by darkod on 2009-12-13
> **blondibee said:**
>   The keyboard on the computer doesn't have a usb plug but it does say keyboard failure during startup. 

If it says failure I would concentrate on the keyboard. Try with another keyboard if you can, PS/2 or USB. This one seems to have problems.

---

