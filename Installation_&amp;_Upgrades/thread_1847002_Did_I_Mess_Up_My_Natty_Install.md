---
title: "Did I Mess Up My Natty Install ?"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by Windows Refugee on 2011-09-20
Did I mess things up ?

I just completed installing Ubuntu Desktop edition 11.04 on a brand new Toshiba NB505 netbook (Really nice machine, BTW).  

During the install process, I resized my Windows 7 Starter edition's C: partition from around 240GB to 200GB, and created a 35GB EXT4 partition for Natty and an approx 4GB swap partition.

Natty appeared to finish installing without any problem, but when I restarted the machine, Windows tried to boot, but complained that the disk needed repairing.  It took a few minutes to do whatever it had to, and then told me to restart the system.

Now, Windows boots up just fine into it's newly downsized 200GB partition, but I never see either the Windows bootloader or GRUB come up.  When I run msconfig, the only OS that Windows knows about is Win 7.

I suspect that my decision to place the bootloader in my newly created 35GB partition during the install process was wrong.  

Can the installation be salvaged by either telling Windows bootloader where Natty can be found, or by reinstalling or moving GRUB to where I should have placed it in the first place ?
(My preference would be to use Window's bootloader.)

Also, from my past installs of Ubuntu on other machines, I seem to remember being given the choice of using the Windows bootloader or GRUB to multiboot, but I didn't see any such choice during this install.  Did I miss something ?

Thanks !

P.S. - Contrary to some other comments I've read online, the install process had no problem installing a driver for this Toshiba netbook's wireless card.  It let me set up my SSID and password, and joined my hidden WPA2/AES network without any problem. Yipee !

---

### Post by Quackers on 2011-09-20
Grub ssould be installed to the MBR of the hard drive, not to the Ubuntu root partition.
You could boot from the Ubuntu live cd/usb and select "try Ubuntu" and when the desktop loads open up a terminal.
Then run ```
sudo fdisk -l
``` (that's a lower case L, not a 1).
This will give details of your partition layout.
You need to identify which partition is your Ubuntu root partition.
You can then run ```
sudo mount /dev/sdXY /mnt
sudo grub-install --boot-directory=/mnt /dev/sdX
``` where /dev/sdXY is your Ubuntu root partition (eg /dev/sda5) and /dev/sdX is your hard drive (often /dev/sda). NOTE no partition number in the second command.

This should report that it has run with no errors.
If it does, reboot and you should then see Ubuntu boot directly. You can then open a terminal again and run ```
sudo update-grub
``` when you should see the Windows Loader recognised. If so, reboot and you should then get a grub menu giving you the choice of which OS to boot.

---

