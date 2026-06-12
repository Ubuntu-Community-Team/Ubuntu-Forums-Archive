---
title: "[LUBUNTU] Lubuntu on Samsung N130"
date: 2015-12-24
forum: Installation &amp; Upgrades
---

### Post by jorge29 on 2015-12-24
Hi
I'm trying to install Lubuntu on a Samsung N130 laptop. I can't get it.
When loading USB live I get black screen with blinking cursor. If I try the compatibility mode, it hangs when appears "ACPI : SSDT    (null) ...", like it's shown on the attached image.
[IMG]https://dl.dropboxusercontent.com/u/34534160/20151224_190055.jpg[/IMG]
I've tryed a lot of linux distros, but no positive results. I would like to install Lubuntu. Anyone can help me?

---

### Post by Vladlenin5000 on 2015-12-24
Hi and welcome.

Samsung N130 is the typical Atom based netbook from 2008/9. There's absolutely nothing special about it and the installation should just work.
So, first things first, is it a known good machine? I mean, have you assured it is working properly (with the original XP)?
And you need 32-bit...

---

### Post by yoshii on 2015-12-25
I tried booting from a USB drive and found that the drive got corrupted easily.  Some of the Puppy Linux people say don't try to install to USB drive, just create a LiveCD or LiveDVD and boot/install from that instead.  Also, you may need to disable ACPI.  ACPI is rather buggy on some systems, especially for Linux.  I don't know how to implement kernel mode commands for booting, but if you can find and enter the no acpi or acpi disabling commands with the right syntax it might boot but without some software control of some power functions.  Also if you disable ACPI you lose hyperthreading unless you use a different disabling acpi command that keeps hyperthreading only.  Search the Ubuntu website for Grub and BIOS command editing and it will give more info on this stuff.  Also, on some machines you have to add a kernel command that identifies the system as Linux instead of Windows.  I will try and come back to post more info if I find the original sources of the info that helped me on my old system.

---

### Post by MAFoElffen on 2015-12-25
On install refer to post #3 in the Graphics Resolution Sticky in my sig line.
```

[COLOR=#333333][FONT=Ubuntu]noacpi[/FONT][/COLOR]

```
On reboot, press the left shift key as you pass the BIOS Messages, then <E> to edit your Grub Boot Menu > same boot option added to the end of the linux boot line > <cntrl><X>
(Instructions linked from post #2 of that same sticky)

Instructions to make that persistent in Post #1 of that same sticky... (edit and update grub's ...)

Edit: :redface: I started that sticky almost 5 years ago. Almost a half million views, and I still refer back to it for the diagnostic instructions and work-around's that I documented there... to help people.

---

### Post by jorge29 on 2015-12-26
Hi Vladlenin5000
First, thank you for the quik reply.
It came with Windows 7 Starter, and worked fine. But lately it was slow.
I've tryed to install Linux Mint, Sparky linux, the old Ubuntu Netbook Remix, Lubuntu... and no way. When I boot with the live USB, it start loading but suddenly the screen blinks and it stops. If I start on compatibility mode the only one that works is Linux Mint, the other give me the screen I show on the first message. The other distros hang on ACPI loading even Live Boot.

---

### Post by Vladlenin5000 on 2015-12-26
I would try the suggestion in the post#4 because it most likely has a bugged ACPI implementation.

---

### Post by jorge29 on 2015-12-26
Hi
I've tryed the noacpi option, and it still hangs on.
I'm trying to install Linux Mint now.
Well, I'll try Lubuntu later.
Thank you

---

### Post by jorge29 on 2015-12-27
Finally I've get it. I've created an USB live with "mkusb" in other linux computer. The live USB get loaded and I've selected the "Try lubuntu..." option with "acpi=off", "noapic", "nolapic", "edd=on", "nodmraid" and "nomodeset". Loaded normally. Then I've installed Lubuntu as usually, and no problem except the resolution: it is at 800x600, and the Samsung N130 gets 1024x600. I've won a battle, but not war.

---

### Post by MAFoElffen on 2015-12-28
Now just go to Ssettings and reset your graphics resolution in "settings." Then please revisit this thread > Use the Thread Tools link in the upper right of the page to mark this thread as "Solved." 

Good Luck and Enjoy.

---

### Post by jorge29 on 2015-12-29
Hi
It was not as easy. There was no other resolution option in settings. The monitor was not identified, so the SO was not properly installed.
So, my first error was not to read. The solution: read, read, read!!!. The last time I installed Lubuntu was " a long time ago.." so this time I didn't knew that I must not to use Unebootin. So I had to make the live USB with MKDISK. It worked, but not fine... I had the resolution problem I descibed above.
So if I change the USB stick?... I've been using a new (just bought) 8Gb trascend USB... What If I use an old 4Gb TDK USB that always give me a lot of errors? surprisingly it worked fine!!!!!! The only option thad I had to add to get runing the live session was "noapic". I don't know what it is, but it worked fine with it. Now I have the SO runing Ok on the little and weak Samsung N130. And It works infinitely better than the Windows 7 starter.
Thank you all very much. Happy new year!!!

---

