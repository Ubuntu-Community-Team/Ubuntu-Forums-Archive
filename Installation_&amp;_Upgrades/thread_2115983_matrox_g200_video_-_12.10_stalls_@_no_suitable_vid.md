---
title: "matrox g200 video - 12.10 stalls @ no suitable video mode found"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by bababooey on 2013-02-14
I have a fairly nice server im using as a workstation(dual xeon 32gb memory) but unfortunately it has a matrox g200 video card built in. I think this old video card is the root cause of my problems getting Ubuntu and Xubuntu 12.04 to 12.10 installed, mainly Xubuntu for xfce. I would prefer to have 12.04.1 LTS installed but I get a message "Building command list" and then a black screen when I try to boot into anything through the live disc in EFI mode(Live Mode, and Install options in grub). Using Nomodeset in grub does not work.

My latest attempt, is installing 12.10 amd64 desktop version. I can actually boot into live mode and complete an install. But upon a reboot I get these messages as it boots

error: no suitable video mode found.
error: no suitable video mode found.
Booting in blind mode

At this point my system does not crashes, it just stalls with this message on screen. I cant get a console using ctrl-alt-f1-f12. The weird thing is that 12.10 live works, but not after i get it installed.

lspci in live mode shows my video card as
VGA Compatible controller: Matrox Electronics Systems Ltd. MGA G200EV

This is my first time working with EFI and wondering if anyone had any luck with Ubuntu 12.04 or 12.10 with the same video card? I had a pci-e video i just sent out for RMA and hope that will resolve all the issues im having but in the meantime I would like to get this up and running.

---

### Post by MAFoElffen on 2013-02-14
> **bababooey said:**
> I have a fairly nice server im using as a workstation(dual xeon 32gb memory) but unfortunately it has a matrox g200 video card built in. I think this old video card is the root cause of my problems getting Ubuntu and Xubuntu 12.04 to 12.10 installed, mainly Xubuntu for xfce. I would prefer to have 12.04.1 LTS installed but I get a message "Building command list" and then a black screen when I try to boot into anything through the live disc in EFI mode(Live Mode, and Install options in grub). Using Nomodeset in grub does not work.

My latest attempt, is installing 12.10 amd64 desktop version. I can actually boot into live mode and complete an install. But upon a reboot I get these messages as it boots

error: no suitable video mode found.
error: no suitable video mode found.
Booting in blind mode

At this point my system does not crashes, it just stalls with this message on screen. I cant get a console using ctrl-alt-f1-f12. The weird thing is that 12.10 live works, but not after i get it installed.

lspci in live mode shows my video card as
VGA Compatible controller: Matrox Electronics Systems Ltd. MGA G200EV

This is my first time working with EFI and wondering if anyone had any luck with Ubuntu 12.04 or 12.10 with the same video card? I had a pci-e video i just sent out for RMA and hope that will resolve all the issues im having but in the meantime I would like to get this up and running.
Please take a deep breath.

So first, some clarity:

You say you are installing Ubuntu or Xubuntu "Desktop Edition" on a computer that has a "server board" that has onboard Matrox G200EV GPU as video right? (G200 intro'ed 1993?) ...And you want to run a graphical desktop environment to use it as a Desktop PC.

That's how I translated what you said...

Reboot. Press the left shift key as you get past the the end of your post messages. That should display your grub menu. Quickly hit the <down-arrow> so the menu receives input and stops the menu display timer.

<up-arrow> back up to the first menu item. Press <e> to get into edit mode. Move the cursor down to the linux boot line and replace "quiet splash" with "vga=772". Press <cntrl><x> to boot with that modified option. That says boot into vga/vesa mode 1024x768x16bit...

If that mode doesn't work (that GPU says it supports up to 1920x1200), then use this option instead, "xforcevesa", which will tell it to explicitly try to force it to use the vesa driver.

If one of those modes works then go to my graphics sticky, linked in my sig line, post #1 and read down to where is tells how to make that change permanent/persistent.

Tell me how it goes, either way.

---

