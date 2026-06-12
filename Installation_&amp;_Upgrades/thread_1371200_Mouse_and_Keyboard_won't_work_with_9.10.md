---
title: "Mouse and Keyboard won't work with 9.10"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by Final Version on 2010-01-03
I'm trying to install 9.10 but I decided to run it live first, my mouse and keyboard won't work. They are both connected via usb.

---

### Post by Tayl on 2010-01-03
I'm also having the same problem. The mouse and keyboard, naturally, are enabled during POST, but once you hit the menu screen from the CD to choose whether or not to install or run the live edition, they die as if not detected. They are definitely supported as (by default) it chooses the live cd to be ran and once booted, the keyboard and mouse work perfectly.

Is there any way to get them both working upon boot up of the cd so you can navigate to install?

Tayl.

**:: Edit ::**

Final Version, are you using any sort of USB hub or are all USB devices plugged directly into your motherboard? Not that it makes a difference as I tried both. What motherboard are you using? And the spec's of the rest of your hardware (CPU etc)?

---

### Post by Tayl on 2010-01-03
**Re-posting to bump.**

Final Version, managed to get mine working after doing a little poking about. Turns out it was something simple that I had overlooked. Go into your BIOS and check that you have USB Keyboard Support and USB Mouse Support enabled. I found it within a section titled: integrated Peripherals, within my BIOS. Enable those and it should work. Worked fine for me. Seems general USB and USB 2.0 Support doesn't include your keyboard and mouse and that you need to enable support for those separately.

Regards,

Tayl.

---

### Post by Final Version on 2010-01-03
Looked under "Integrated Peripherals" found nothing of the sort, also looked around hoping to get lucky, but failed :( Oh and I'm using an Acer Aspire M1640.

---

### Post by Final Version on 2010-01-03
Bump.

---

### Post by slooksterpsv on 2010-01-04
Check your BIOS settings, sometimes the USB may be turned off in there until the OS loads to use it. My friend had that problem with his Dell and Ubuntu - USB was turned to Off I think and when the OS loaded it would switch on the USB (the computer didn't have any PS/2 Ports on it it was full USB).

If that doesn't work, try Fedora, that OS is really nice.

---

### Post by Tayl on 2010-01-04
Are you positive that all options within your BIOS that relate to USB controllers are set to 'on' or 'enabled'? Double check to make sure as sometimes it can be easy to miss. Anything with USB in the title just enable. Even if it's not for the keyboard and mouse specifically, it won't harm. However I am pretty sure it's an option in your BIOS that needs to be enabled.

I assume that if you let it default and load up the Live CD, that your keyboard and mouse work then once that is booted?

Regards,

Tayl.

---

### Post by KeLa on 2010-01-04
It might be "USB Legacy support setting" in BIOS that must be enabled.

---

### Post by Final Version on 2010-01-04
I'll have a good look through my bios.

---

### Post by Final Version on 2010-01-04
Ok, anything to do with USB is enabled. Still exactly the same though.

---

### Post by Tayl on 2010-01-04
Let it default boot up the Live CD and let us know whether or not your USB devices are working once the Live CD has automatically loaded (to make sure that your USB controller is supported).
[I][COLOR="Silver"]
Someone correct me if I'm looking in the wrong place.[/COLOR][/I]

Tayl.

---

### Post by Final Version on 2010-01-04
As soon as I hit either "Try Ubuntu" or "Install" they fail.

---

### Post by slooksterpsv on 2010-01-06
Have you checked for a BIOS update?

---

### Post by Final Version on 2010-01-06
I'd rather not flash any bios's just to install 9.10.

---

### Post by Final Version on 2010-01-06
Bump.

---

### Post by Final Version on 2010-01-07
Bump.

---

### Post by Final Version on 2010-01-07
Bump?

---

### Post by Final Version on 2010-01-07
Bump.

---

### Post by Final Version on 2010-01-07
Bump!

---

### Post by Final Version on 2010-01-08
Bump.

---

### Post by Final Version on 2010-01-08
Bump.

---

### Post by Final Version on 2010-01-08
Bump.

---

### Post by Findeton on 2010-01-08
I've got a samsung R40 laptop. When I run the live 9.10 ubuntu, everything is fine, but after installing it into the HD, the keyboard, mouse and touchpad stop working (well, as in the terminals I can only use the keyboard, I can only assure that the keyboard was working) as soon as the X server starts (it makes no difference to use kde or gnome). I can't even go to the cntrol+alt+Fx terminals. The keyboard and touchpad are the ones that come integrated in the laptop (ie: no USB). The system, however, is not completely blocked: if I press the shutdown button of my laptop, the system goes back to one terminal and shut downs normally the computer... 

Any piece of advice is welcome!

---

### Post by Final Version on 2010-01-08
> **Findeton said:**
> I've got a samsung R40 laptop. When I run the live 9.10 ubuntu, everything is fine, but after installing it into the HD, the keyboard, mouse and touchpad stop working (well, as in the terminals I can only use the keyboard, I can only assure that the keyboard was working) as soon as the X server starts (it makes no difference to use kde or gnome). I can't even go to the cntrol+alt+Fx terminals. The keyboard and touchpad are the ones that come integrated in the laptop (ie: no USB). The system, however, is not completely blocked: if I press the shutdown button of my laptop, the system goes back to one terminal and shut downs normally the computer... 

Any piece of advice is welcome!
Thread Hijack?

---

### Post by Findeton on 2010-01-08
> **Final Version said:**
> Thread Hijack?

I thought it might be a related problem. Maybe I am wrong...

---

### Post by Final Version on 2010-01-08
> **Findeton said:**
> I thought it might be a related problem. Maybe I am wrong...
You haven't got the exact same problem, so make a new thread.

---

### Post by slooksterpsv on 2010-01-10
Have you tried disconnecting them, then reconnecting them when the LiveCD is loaded?

Do you have access to any of the TTYs, like CTRL+ALT+F1 or that? What about num-lock lights?

---

### Post by Final Version on 2010-01-10
Trying the above now.

---

### Post by CPUDave on 2010-01-10
Basically a similar problem here, The Keyboards and mouse do work in the Live CD but after install and reboot, they are both turned off. Nothing works.

AMD Athlon 64 X2 3800+ PS/2 Keyboard and mouse

Everything else seems OK but how would I know without the keyboard or mouse.

The keyboard turns off right before the first Ubuntu screen. The Numlock will go off and then nothing

---

### Post by him610 on 2010-01-14
I am also experiencing unresponsive mouse and keyboard using 9.10; however, mine both have PS2 connectors. The only way out of the unresponsive state seems to be to reboot the system which is entirely unsatisfactory. 

What do we know?
System specs exceed minimum recommended requirements.
Worked OK in 9.04,
works OK using a live CD.
After upgrading to 9.10, boots OK; after bringing up a Terminal, typed in a couple of commands, got responses on the terminal screen then the mouse and keyboard cease to respond.

Why is this happening?
Resource conflict?
Program in an endless loop?

---

### Post by CPUDave on 2010-01-17
After checking into this, I have reverted my pc back to 8.10 AMD 64 version.

There are numerous bug reports with this and similar problems that remain unresolved. This is the kind of problem that keeps WinDoze alive and limits the expansion of Linux.

It should be noted that statistically less than 1 percent of people with a problem will report it, most just go back to what ever they had before or move on to something different.

bug report    Bug #335297 is one of dozens of similar complaints that start with 9.04 and continue with 9.10 .

my page: [www.david-etheredge.name](www.david-etheredge.name)

---

### Post by CPUDave on 2010-01-28
Solution, not a good one though.

Re-install until it works. The forth try for me worked for keyboard and mouse but there are still several issues including instability.

---

### Post by bottomtop on 2010-02-02
Just thought I would chime in to say "me too".  I am also using an Acer desktop system and neither the keyboard or mouse work once I get beyond the Grub bootloader.

Interesting observations:
No Num Lock Light
Pressing caps lock/num lock etc don't activate lights.
The red light on the bottom of the optical mouse (also USB) will not come on, nor be activated by movement.  

It's like the whole USB controller is completely invisible to the system.

---

### Post by trixx on 2010-04-04
Me too... Acer system as well, usb ports. Funny thing is though, this reinstall, power at least gets to the wireless receiver for my keyboard. Still none to the wired laser mouse though.

---

