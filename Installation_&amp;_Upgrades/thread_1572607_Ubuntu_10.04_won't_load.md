---
title: "Ubuntu 10.04 won't load"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by tomreid on 2010-09-11
Hi

I booted my HP Pavilion a6750t Desktop from a 10.04 "Live CD" (in this case a live USB stick) and it all seemed to work fine off the live cd.

I used Gparted to delete all the partitions on the HD and leave it as free space.

I installed Ubuntu, and the install seemed to go as normal. I chose the option to erase and use the entire HD from the partition manager when I was doing the install.

All seemed to go fine, but when I went to re-boot the system, Grub does not load, I get a flashing cursor for a few seconds, then the monitor goes to sleep. When I force the monitor back on it searches for a signal, can't find one, then goes back to sleep again.

I suspect that 10.04 is not booting at all. 

Very strange. Previously this system was running 9.10 fine.

Please help, I am completely stuck.

cheers

---

### Post by ronparent on 2010-09-11
Since the Ubuntu is the only system now on the computer, the grub boot manu won't show on the screen. That may be the starting point to see why it doesn't boot. Hitting any key once your bios screens have processed should bring up the menu (ie just hit space bar repeatedly - maybe half second intervals).

If you can get the menu, hit <e> (to edit) and move the cursor to the kernel boot line. Backspace to delete quiet splash. Wher the boot process stops may give a clue as to what is stopping the boot. Post what you find and someone can try to helo interpret the results.

---

### Post by Rubi1200 on 2010-09-11
What graphics card do you have installed?

---

### Post by tomreid on 2010-09-11
Yes I suspected a corrupt GRUB was the problem. I had problems before and thought that using Gparted to make the hard drive all free space would delete the old grub a new grub would install when i re-installed 10.04, but this obviously didn't work. 

Unfortunately when i get past the bios screen, when i hit any key to try to get into the Grub to edit it, nothing happens. 

Except, (for example) when I hit an "e" then an e appears on screen, then the screen goes black again.

Any other ideas about dealing with a corrupt Grub? Where on the hd is grub installed?

cheers

---

### Post by Rubi1200 on 2010-09-11
First, can you tell us what graphics card you have?

Second, boot with the LiveCD and post the results of the bootscript linked to at the bottom of my post.
If the issue is really with GRUB it should hopefully show up in the results.

Thanks.

---

### Post by tomreid on 2010-09-11
Hi

Thanks a lot for your help.

The spec of the graphics card is below.

The results of the bash script are in the attached text file.

cheers

[COLOR=#333333][FONT=arial]•  256MB NVIDIA GeForce 9300 [DVI, HDMI, VGA adapter][/FONT][/COLOR]

---

### Post by ronparent on 2010-09-12
The fact that you had booted to a live cd with no problems should assure that the installed system should also boot. Nothing stood out in your result.txt file. Since you have relatively little invested in your clean install it might make sense to wipe everything and install again. Before doing that a quick grub reinstall from the live cd might be worth a check. When booted to the live cd, open a terminal and reinstall grub2 per this reference: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2 

Basically you will be entering:

> sudo mount /dev/sda1 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda

Cut and paste would give you assurance the commands are written properly. Reboot after running them. If you still cant boot,   check your disk for error, wipe your partitions and reinstall. Post if you have more problems.

---

