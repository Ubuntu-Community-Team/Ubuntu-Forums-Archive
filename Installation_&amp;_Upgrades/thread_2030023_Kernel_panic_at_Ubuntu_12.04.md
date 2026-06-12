---
title: "Kernel panic at Ubuntu 12.04"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by rophys on 2012-07-20
Hi all,

I just bought a Sony Vaio series S (8gb Ram, i5 3rd generation) and during the Ubuntu instalarion it gave me the following mensage : "Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)" "Pid: 1, comm: swapper/0 Not tainted 3.2.0-23-generic #36-Ubuntu.

Anybody can help me to solve this problem ? Any tips ?

Cheers.

---

### Post by EboMike on 2012-07-31
That's because of EFI. Here's your solution - reboot the laptop, and as soon as you see the VAIO logo, tap F2 until the BIOS menu appears (seems to be very tricky - try a couple of times. If you see a boot menu that lets you choose Windows 7, you missed it and have to restart).

In the boot menu, go to the load options on the right (not sure about the actual name of the menu item) and change the top option from "EFI" to "Legacy". That should do.

---

### Post by rophys on 2012-08-10
EboMike, 

I tried the option "Legacy" (instead UEFI) of in the boot menu but when I restarted the laptop it gave the message "Operating System not found".

If somebody found the solution for this...please post here.

Many thanks.

---

### Post by EboMike on 2012-08-11
Did you enable booting from CD in the BIOS options (with the CD having higher priority)? Was the CD in the drive?

---

### Post by rophys on 2012-08-13
EboMike, thanks for this !

I manage how to install Ubuntu 12.04 in my sony vaio.
I just changed the UEFI by Legacy and also changed the priority of boot (optical drive).

---

### Post by EboMike on 2012-08-13
Haha, don't thank me yet - the biggest challenge is still ahead of you: Make the graphics adapter work. That took me three days.

Whatever you do, DO NOT install the Nvidia driver up front. It will replace your existing drivers and eliminate your ability to use the Intel chipset (I suppose your laptop has the Optimus, which means you have both Intel graphics and Nvidia graphics).

You'll need to install Bumblebee. Ideally, that takes care of everything.

I got it to work eventually by rewiring some files (details here: [http://askubuntu.com/questions/171470/how-to-make-unity-3d-work-with-bumblebee-using-the-intel-chipset](http://askubuntu.com/questions/171470/how-to-make-unity-3d-work-with-bumblebee-using-the-intel-chipset)).

All I can tell you is that it is possible to run the laptop the way you want to - using the power-saving Intel graphics acceleration for Unity, and using the powerful Nvidia chipset on demand when you want to run something graphics-heavy.

In fact, I'd almost say that it's even better than on Windows, where you have to switch between those two using a physical switch on the laptop.

---

### Post by rophys on 2012-08-13
Hi EboMike,

Everything is running well in my laptop...I tried to avoid the the graphics cards with Optimus because some of my friends already hd problems with it trying to install Ubuntu. Actually my graphics card is a Intel 4000. Until now it is enough for my work =).

I'm having a new problem now (instead of graphics card). When I restart the laptop the Ubuntu works just if the Legacy mode is activated. If I want to use the windows I need to use the UEFI mode. It is very annoying to enter in the boot mode and change it all the time. How can I restore the dual boot ? I already tried the Windows CD (recovery mode) but didn't work.

---

### Post by EboMike on 2012-08-13
I'm afraid you're where I am at this point. It doesn't bother me - I only ever boot into Windows once in a blue moon (a sandbox inside VirtualBox is typically good enough for me).

I hope that Ubuntu 12.10 will fix this, Canonical is actively working on compatibility with UEFI. This is not a trivial matter though, so I wouldn't be surprised if we might have to wait longer.

---

### Post by rophys on 2012-08-14
That's perfect eboMike. The most important thing is...my Ubuntu is running perfectly even using the Legacy bios. Also I don't access the Windows very often. Thanks anyway for your tips and if you know something how to solve this boot problem, let me know ok ?

Cheers

---

