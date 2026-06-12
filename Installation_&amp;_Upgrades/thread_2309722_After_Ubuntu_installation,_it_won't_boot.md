---
title: "After Ubuntu installation, it won't boot"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by guillermo15 on 2016-01-13
Hi there.

First off, I'm completely inexperienced. So please, be gentle.

For a specific reason (an accident, I'm afraid), I managed to erase my Hard Disk Drive on my HP ProBook 4545s with an AMD A8-4500M APU with Radeon(tm) HD Graphics processor type. Now, of course, there's no Operating System on it. (Apparently) 

Now, I need to find a new Operating System.

A bunch of people (inside and outside the Internet) recommended me Ubuntu. So, with the help of the good humans inside the Internet, I manage to make a USB stick bootable (I apologize if I use or write some terms incorrectly), I downloaded an ISO file from Ubuntu's website that contained "Ubuntu 14.04.3 LTS", and installed it on my laptop (a process which took me for about eight to twelve hours, due to my lack of experience). Now, after cheers and whoops for finally being able to install it, the Operating System prompts me to restart my computer and I do as I'm told. 

But, alas, after Startup, I'm send yet again to the menu where I have the options of "trying Ubuntu before installing", "install Ubuntu", "OEM install (for manufacturers)", and "Check disc for defects"; as if I didn't installed the Operating System at all just moments ago. I try the last option, in order to check if there is some type of problem with my USB stick, and it says it's okay. So, what is it then? Note, I tried installing it again and in the installation process it was recognized that Ubuntu was already installed, and offered me to erase it and install Ubuntu (again).

I tried playing with the BIOS Setup settings, see if it isn't Legacy, then it's probably UEFI Boot Mode, etc. Nothing. I tried booting from EFI file, the GRUB menu, nothing. Even tried using that "nomodeset" thing some of you suggested on other threads, and nothing.

Now, I can't simply loose that laptop. I'm having an Algorithm class this semester, and I terribly need it for the course. I have a strong feeling that my laptop is fine, that I just need to try a minor detail that I haven't figured out yet, and probably Ubuntu will boot (just as my last Operating System, Windows 7, used too). I'll be very grateful for any suggestions.

Thank you for your time on reading this. Have a good day.

---

### Post by deadflowr on 2016-01-13
Remove the usb stick and try it...

---

### Post by kevdog on 2016-01-13
Do you know you have UEFI boot?  The reason I'm asking this is because setup with this type of system is more complex and prone to problems.  There are definite work arounds however it does take some trial and error.

---

### Post by Bucky Ball on 2016-01-13
> **deadflowr said:**
> Remove the usb stick and try it...

+1. Welcome. When it says it is installed, which it did, pull the stick and reboot. You might want to hit F12 at boot, which gets you to a boot device menu on most machines, and choose the hard drive to boot from.

PS: Don't go changing EFI/Legacy in the BIOS. Leave it exactly as it was when you installed Ubuntu or you are looking for trouble. :)

---

