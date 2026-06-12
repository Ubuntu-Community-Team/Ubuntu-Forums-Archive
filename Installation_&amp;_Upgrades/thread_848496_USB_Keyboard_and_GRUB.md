---
title: "USB Keyboard and GRUB"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by dugonline on 2008-07-03
So I have been in Ubuntu 100% since the release of Hardy.  I have found that I can run most of the Win programs I still require in WINE or Virtual Box with little to no errors.  Unfortunately there are still a few Windows apps that I need to run at this time until I find better options in Linux.  So I have started the process to go back to a Dual boot leaving only 10 gigs for the Windows Partition.

I had done this previously using Ubuntu 7.10 and had no problems on this same computer.  But now, when I load GRUB it won't see my keyboard.  I can get into the Bios and such, and the keyboard works great but I can't select with OS I want to use.  I have looked through a number of blog posts, forum posts and this seems to be a regular issue.  The only real solution is to not use the USB keyboard.  This is not an option for me.  I have a PS/2 keyboard, I have a bunch of them.  But this particular keyboard is pricey and large.  I don't have small hands and so typing on small regular keyboards is a pain, which leads to laptop keyboards being near impossible for a lot of typing.

I don't want to instal 7.10 if I don't have to, I like 8.04 and got used to the changes. I like Hardy a lot.  I can do all my work inside Windows, but I don't want to.  I can't do ALL my work in Linux at this time, and until I can dual boot is gonna be my only option.

I must find a solution to this or be forced to revert to 7.10.

Can anyone help?  I have set and reset my keyboard in BIOS and I have tried anything else I can think of.

Thanks in advance for any help

DUG

---

### Post by Pumalite on 2008-07-03
Have you tried changing of USB port after the boot?

---

### Post by dugonline on 2008-07-03
Do you mean boot with a PS/2 and then change to USB after the boot?  Cause I thought about doing that, but I don't want to get behind my computer every time I want to turn it on, reset or etc.

Otherwise I don't follow.

---

### Post by Pumalite on 2008-07-03
No; boot with your USB plugged. After the boot; when the arrow remains immobile, change your keyboard to a different USB port.

---

### Post by estyles on 2008-07-03
I have the same issue.  I haven't tried Pumalite's suggestion, but I will as soon as I get home tomorrow morning.  My solution is to simply plug in two keyboards.  The second keyboard is plugged into the PS/2 port and leaned up against the side of my desk.  When I need to access the Grub boot menu (a rarity now that I've set my computer up to automagically boot from linux->windows and from windows->linux), I grab the auxillary keyboard and use it up until choosing the OS.  Only becomes a problem if I lean it back wrong and a key is stuck down and I don't understand why my computer's going crazy.

Another solution would be to use a USB->PS/2 adapter.  I've done that in the past when my USB mouse wouldn't work correctly in Windows.

---

### Post by bigken on 2008-07-03
> **estyles said:**
> Another solution would be to use a USB->PS/2 adapter.  I've done that in the past when my USB mouse wouldn't work correctly in Windows.


this has to be the easiest solution

---

### Post by Pumalite on 2008-07-03
If the motherboard has a PS/2 connection; I agree.

---

### Post by dugonline on 2008-07-03
I do have a conversion for the USB to PS/2 conversion, but then I lose features on the keyboard.  I have a Logitech G15 and I am quite spoiled by it really.  If worse comes to worse, that is the route I will choose however.

Thanks to all for your advice.  I was hoping to find out there is an updated GRUB or something out there.  I didn't have this problem with 7.10 so I find it odd that is exists in 8.04.  In the end, it is what it is right?

---

### Post by gluer_2 on 2008-07-06
I had the same problem recently because i just bought a usb keyboard. i found the solution on one of the threads here. what i did was go to my bios setting and looked hard enough for USB keyboard support and i enabled it. Since i'm using an ECS motherboard, i found it under the USB Emulation setting. I think yours had some equivalent setting. After enabling it, Grub accepted input and i was able to choose from it. btw, i also dual boot hardy and windows.

---

### Post by estyles on 2008-07-06
> **gluer_2 said:**
> I had the same problem recently because i just bought a usb keyboard. i found the solution on one of the threads here. what i did was go to my bios setting and looked hard enough for USB keyboard support and i enabled it. Since i'm using an ECS motherboard, i found it under the USB Emulation setting. I think yours had some equivalent setting. After enabling it, Grub accepted input and i was able to choose from it. btw, i also dual boot hardy and windows.

I second this.  I thought that it couldn't be a BIOS problem, because the BIOS recognized my USB keyboard fine, but I found the answer probably in the same thread gluer saw.  The BIOS apparently gives up control of the USB keyboard after it gets past the "press DEL to enter configuration" screen, expecting the OS to take care of the keyboard, since "USB keyboard" support was disabled in the BIOS.  Since Grub loads before the OS, there was nothing driving the keyboard.  Enabling USB keyboard support in the BIOS fixed my problem.  To the OP - if it doesn't fix your problem, then I do suggest simply connecting a second (PS/2) keyboard and using it just for the boat loader menu.

---

### Post by dugonline on 2008-07-06
I thought I had tried the BIOS option, but perhaps there is something I am overlooking somewhere.    I will be trying again tomorrow night!

Thanks everyone for the comments, and keep em coming!!

---

