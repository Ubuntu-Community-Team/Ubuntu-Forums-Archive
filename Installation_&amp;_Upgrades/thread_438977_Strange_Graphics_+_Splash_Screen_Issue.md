---
title: "Strange Graphics + Splash Screen Issue"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by ccerinojr on 2007-05-10
Howdy,

This problem is extremely odd, but before I get into that here are my system specs:

Processor: AMD 64 3400+
Memory: 2 Gigs
Graphics Card: ATI X850XT AGP ( Dual monitor setup)
Motherboard: ASUS A8V Delux

Right, now on to the problem. I am able to install Ubuntu 7.04 onto my system via the alternate 64 bit installer cd. After the install completes and the computer restarts, you see Grub. The next thing you would expect to see would be the Ubuntu loading splash screen, but this never appears and my monitors go into sleep mode. I did some poking around and found a post that mentioned editing kernel line in the menu.lst file in /boot/grub by changing splash to nosplash.

I booted into the recovery console, made the change, rebooted, and BINGO! I log into Gnome for the first time and it kindly asks me if I would like to install drivers for my card, sweet! The drivers successfully installed, and I went to reboot the system as prompted. After clicking the restart button, my monitors go into that sleep mode, and after a few minutes of waiting my computer never reboots. This should not be the case. I am pretty sure you should see some info about ubuntu shutting all of your stuff down.

I kill the power and power it back up. Once it boots I log back into X, and I am glad to find that fglrx_info is outputting the correct information to show that the drivers were properly installed and working. Following my curiosity I go and attempt to restart my system again, and I am met withe the same problem as befor. 

I did some more digging, and I found another post that suggested editing the kernel line in the menu.lst file by having it set to splash and adding vga=795. I make the change and restart. This time after grub appears, I am presented with a distorted and an off positioned splash screen, but after the splash screen goes away I do not get X and my monitors go into sleep mode.

Summary:
 [LIST]
[*]Splash screen and booting to X does not work out of the box. It works if I edit the kernel line in grub's menu list to have nosplash.
[*]ATI drives install and work fine.
[*]Editing the kernel line to have nosplash causes restart, logout, shutdown, etc.. to not work.
[*]Editing the kernel line in menu.lst to have splash and vga=795, shows a distorted splash screen, but it does not boot into X. 
[/LIST]

I have spent a good part of last night attempting to hunt down solutions in the forums. I apologize if this is something extremely simple or there already exists a solution for this answer. This issue is extremely perplexing and I would appreciate any help from this awesome community. 

Cheers,
ccerinojr

---

### Post by snak63 on 2007-05-10
I am having the same problem as yours and I am starting to think it has something to do with the initial resolution of the graphics card (I have an Ati x800) when I first loaded the live CD it failed and like you my monitor shut down. On the second attempt I checked the resolution with F4 and found it was set massively high. after I changed it to 800 x 600 32 every thing worked well but after installing and rebooting it crashed again so I'm wondering if it didn't save the change and defaulted back to it's original. If you find any soulution to this pleeeese let me know thanks

---

