---
title: "Trying to install Xubuntu but have problems with boot"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by nealmohanp on 2008-04-08
Iam trying to install xubuntu on a system with 800mhz processor, 256mb ram, and 80gb harddrive. The problem now is it already has windows xp. Ive installed ubuntu before on my other pc but for this one i cant get the cd to boot. I put in the cd and start the computer and after about 30 secs it starts windows xp. Now i cant get in the bios to check what the boot opion is because it is password protected and i dont know the password. Any suggestions?t

---

### Post by Pumalite on 2008-04-08
You have to use the Alternate Xubuntu CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
You need 340 MB of RAM a Live CD.

---

### Post by nealmohanp on 2008-04-08
it says 128 on the website any way...but im not sure i can boot because im not sure the settings in bios has boot enabled. ANy ideas on how to get into bios?

---

### Post by Pumalite on 2008-04-08
At boot, you hit 'Del' or 'Tab' or F2, etc. You can consult your motherboard Manual.

---

### Post by nealmohanp on 2008-04-08
ya i got in but it is protected by a paswword (of all things ](*,) i dont know the password cause this system was my uncles he gave i tto me andhe doesnt know the password. I also know that the cd has a windows  ubuntu  boot installer(or somethin lik ethat) but i cant use it because my xp(crap of a machine) is full of viruses and wont let me go past the login screen.

---

### Post by bdailey on 2008-04-08
I would back up all my data before trying this but as a last resort you could flash your bios by unplugging the computer and removing the backup battery located on the motherboard for a few seconds and the reinserting the battery. On most motherboards this will put the bios back into the default state sans password. There also may be a jumper on board that will flash the bios back to default but without the manual I wouldn't mess with the jumpers.

---

### Post by nealmohanp on 2008-04-08
Ill try that...i just hope the default password is somethin like 000000

---

### Post by plucky on 2008-04-08
You probably have a floppy drive on that system,and the BIOS is probably setup to boot from the floppy first. You could create a boot floppy using Smart Boot Manager.

If you load the Xubuntu Cd  on an Ubuntu system and when it automounts,you navigate to the **installs** folder,you will find a file called **sbm.bin**. This file is an image file of Smart Boot Manager.Copy the file to your home directory.

To create the floppy with Ubuntu,open a terminal and use ```
dd if=sbm.bin of=/dev/fd0
``` and this will copy the SBM image to a floppy drive and it will be bootable.

You should be be able to use a program called **rawrite** under windows to write this file to floppy,but I have never used it so don't know how it works.


Good Luck.

---

