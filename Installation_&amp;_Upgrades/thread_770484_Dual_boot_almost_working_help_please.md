---
title: "Dual boot almost working help please"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Fenris_rising on 2008-04-27
hi all
after a couple of days i have managed to install 8.04 as a dual boot with XP Pro. now my only problem is that when i select Ubuntu from the OS options it starts to boot then went to the initramfs busybox. i managed to work out with the help of info on this forum that pci=nomsi would help and it does. when i boot ubuntu i go into the menu option and edit a line by adding the pci=nomsi. then i boot up no problem. however it looks like i have to do this every time i boot up. so how do i make this a permanent fix?
other than that everything seems to work flawlessly and i like it better than XP.
I installed Ubuntu using the option install within windows when in XP.
my system is

A8V-VM motherboard
AMD3200+ CPU
1G DDR400 Ram
SATA HDD 80GB (OS's are on here)
IDE HDD 80GB storage drive.

thanks in advance

Fenris

---

### Post by Pumalite on 2008-04-27
Edit /boot/grub/menu.lst and add it to the boot line; something similar to this:
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=679f828a-c798-4e3c-85db-5ac075588271 ro quiet splash

---

### Post by Fenris_rising on 2008-04-27
hi there
thanks for that. i have done as you said. however it hasnt done the deed. i rebooted again and went into menu and had to edit that line. my adition doesnt show but when ubuntu booted up i checked the menu lst and my addition is there.splash this is how i addeded it; 
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=679f828a-c798-4e3c-85db-5ac075588271 ro quiet pci=nomsi.

did it need a / as well or should it have been edited with a specific app. i used open office.

pardon my stupidity, ive just had another look and i had edited the safe mode option. i have now just added the nomsi argument to the correct line and my god it works. ive had a good day, even got realplayer working and i can run my windows based PCB software with wine...........i think i should get a bigger hard drive 160GB and split it 50/50. loving this experiance thanks for your help.
regards

Fenris.

---

