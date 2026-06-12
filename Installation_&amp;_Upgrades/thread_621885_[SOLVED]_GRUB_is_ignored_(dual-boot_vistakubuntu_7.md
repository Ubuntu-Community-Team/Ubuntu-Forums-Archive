---
title: "[SOLVED] GRUB is ignored (dual-boot vista/kubuntu 7.10) on HP desktop"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by bfury on 2007-11-24
Hi,

I just bought a new PC (HP Pavilion m9070.fr), that came with Vista installed on. I installed Kubuntu 7.10, with GRUB installed in the MBR of the HDD.

Believe me or not, when i switch on the computer, GRUB is ignored, Vista boots automatically after the "HP" screen.

If i reboot, Grub is launched the right way. This only occurs when i switch on the computer.

I tryied to install Kubuntu alone on the PC, but GRUB is still ignored when i switch on the PC, "Missing Operating System" alert displays on the screen. And then, if i make a "ctrl+alt+del", GRUB is launched at reboot.

It seems like there's something in HP Bios that looks for a vista partition, ignoring the bootloader, but there no option to change this in the Bios Menu.

I read a lot of posts about "tattooed HDD" legend, but i don't think that's the case, i had no problem to restore from HP rescue discs.

Does anyone have an idea?

Thanks in advance.

Laurent

---

### Post by Pumalite on 2007-11-24
Before you install Ubuntu, you have to allow space for it with Vista partitioner; otherwise Vista will not let you run anything in that computer.

---

### Post by bfury on 2007-11-24
Hi Pumalite,

Yes, the second time, after i used HP rescue disc, i then reduced my Vista partition using the Vista disk manager before i installed Kubuntu. (the first time, i had used G-parted).

---

### Post by Pumalite on 2007-11-24
Your 'hidden recovery partition' at the front might be the problem. Get a Knoppix Live CD: 
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Boot from it and from the Terminal, post:
sudo fdisk -lu
cat /boot/grub/menu.lst (from partition that contains /boot)

---

### Post by bfury on 2007-11-24
Here are the outputs of each command (launched from kubuntu shell, since knoppix 5.1.1  doesn't support my network card, no way to post them out from knoppix).

But i must say that the recovery partition is not hidden, i can see it from Vista and Kubuntu (/dev/sda2). Hp says that you even can erase it once the rescue discs are generated.

---

### Post by Pumalite on 2007-11-24
Get a Gparted Live CD:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and change the bootflag to sda3. Let's see what happens.

---

### Post by bfury on 2007-11-24
Well i tried, but nothing changed : i switched off then i switched on and it had booted under Vista ... But ... I find out that each time that i switched on the computer (and each time GRUB was ignored) the Bios HP screen displayed a longer time, accessing to my External USB HDD.
Then comes the strange part (and i just can't believe it's a real solution), i tried to switch on the PC with the external drive unplugged, and GRUB was launched each time... So i get back to Bios options, and made some changes to the boot sequence.

Setting works with an order of device classes :
1st to boot : Floppy Group
2nd to boot ; CD-rom Group
3rd to boot ; HDD
And in each group, you can order devices.

As the PC has no floppy drive, i set the Floppy group to third place, and in HDD group, my USB external drive was in second place, i simply inactivated it, so it won't be accessed at boot time.

It seems to work ... but i must admit that it should just be a coincidence... 

I get back to you and post here again if i have problems again (next days will say if it is solved or not).

Thanks for all your advices, Pumalite

---

### Post by Pumalite on 2007-11-24
You are welcome. But, you are right . If I had known earlier it would have been the first thing to recommend you. Good luck. Just don't boot with your external turned on.

---

