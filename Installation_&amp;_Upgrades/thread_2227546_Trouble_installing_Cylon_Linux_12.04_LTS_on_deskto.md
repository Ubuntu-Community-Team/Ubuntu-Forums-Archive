---
title: "Trouble installing Cylon Linux 12.04 LTS on desktop (looping boot animation)"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by Crypt96 on 2014-06-02
This is not my first time installing a system.  I have plenty of experience installing and maintaining a Linux system.  I have installed and ran servers on Linux Mint machines, and I love Cylon Linux for its many preinstalled programs.  BUT THIS is the first time i ever had trouble installing a Cylon Linux system on a machine.  

In detail, the desktop:

This desktop has an ASUS P4P800-E Motherboard with a CD drive, 6 USB ports, 4 on the motherboard and 2 more extra on the front.
The desktop runs on a 3.2Ghz Pentium 4 Processor, with two 1GB RAM cards, and an 1.5V AGP video card.  250GB HDD.  USB Wi-Fi Adapter.

The desktop is pretty solid and stable,  I have ran Windows XP and Cylon on it before.

I want a fresh install of Cylon, so I burn a fresh new install CD on my main computer.

The problem lies when I put in the installer CD for a fresh install of Cylon Linux.  The hard drive is not native to this desktop because I wanted to have a Larger sized hard drive to play with.  The hard drive is functional and so are all the parts to the desktop.  When the install CD reads, I am taken to the first time grub menu that states to boot into the live CD, Safe Graphics mode, directly go into the installer, or boot on the HDD.  I proceed to the live CD boot option and the CD reads, and reads, and reads.  I know that it will take a while, so I wait, and the boot animation proceeds; however, that is all the happens in the next 10 minutes, a boot animation.  The CD even stops reading, and I didnt noticed it stopped reading until I look at it directly.  The boot animation proceeds and the CD still spins, but it is not reading.  

In fear of a broken CD drive, I replace it, and try again.  To no avail do I successfully break free from the boot up animation.  I tried every CD drive I own, four CD drives, with the same ending.  Maybe the install CD is broken,  So I burn a new one.  And repeat the previous steps.  Same problem.  Looping boot animation, and it stops reading the disk mid way into the boot animation.  I try selecting another option in the Grub menu, maybe the installer directly?  Ditto, looping boot animation, CD stops reading, but not spinning.

ok... maybe CD drives wont work?  USB install?  I create a USB installer and turn on USB Legacy and set the USB data transfer rate from 12Mb/s to 480Mb/s.  I plug in the USB, Boot up the computer, and repeat the previous steps.  Same symptom with selecting every option on the grub menu.  USB install doesnt work either.  Looping boot up animation, and USB stops blinking, indicating that it is not sending data, mid way into the boot up animation.

*sigh*  what a trip.  Next step?  Lets try another Ubuntu system, maybe 14.04?  just to see something, anything?!  Different symptom.  It boots up to the pink/purple background looking part, and the computer resets and boots the the HDD.  I dont know what to make of it.  Returning to Cylon, I search the forums, and flipped a few pages, and I couldnt find the same symptom.  

I want to fresh install Cylon Linux, but I am unable to on this desktop.  Help?

---

### Post by Crypt96 on 2014-06-02
[WORK AROUND]

I found a work around, but I dont know what will happen in the long run.  I took the 250GB HDD and used some fancy tools to plug it in via USB on another computer and told the installer CD to install Cylon Linux and all its components, grub, third party software, and linux swap on the 250GB HDD.  To avoid overwriting my current hard drive on my laptop, I unplugged the 1TB HDD form the laptop and used only the USB drive to the 250GB HDD for the desktop.  I ran the CD and installed system on the 250GB HDD but the bad part is that the system keeps saying "incomplete build" when booting up on the desktop.  And the graphics drivers are for the laptop, but i removed them manually, and installed the proper ones.  It also says that the Wi-Fi adapter is not connected and the USB Wi-Fi adapter is said to be a wired connection. (strange)  but the system was installed on a separate laptop and booted successfully with minor problems on the desktop.  

I still wish to find a way to clean install Cylon from the desktop.

---

