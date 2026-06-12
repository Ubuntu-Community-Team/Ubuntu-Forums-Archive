---
title: "Restore 98SE/2000 Master Boot Record!"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by phend-one on 2005-06-18
I tried to install ubuntu just now and I messed it up. I installed GRUB on the MBR of the first drive (which was supposed to be untouched, and carries my Windows98SE and Windows2000 dual boot system.

Basically it looks like this:

Channel-1
Master HD
-Windows98
-Windows2000
Slave HD
-WindowsXP

Channel-2
Master HD
-ubuntu

For some reason, when I did a BIOS update, it updated some HD controlling function that can allow the different hard drives above to be set as a virtual booting drive. Eg: Selecting MasterHD on channel one will only show 98/2000. Selecting SlaveHD on channel one will boot straight into XP. And MasterHD Channel two was suppposed to have ubuntu, but when GRUB came along, it wrote to the MasterHD of channel-1.

So basically I need to "undo" or "fix" what GRUB did to that drive and make it able to boot into 98/2000 again.

HELP! Thanks in advance!

---

### Post by jsuen on 2005-06-18
[QUOTE=phend-one]I tried to install ubuntu just now and I messed it up. I installed GRUB on the MBR of the first drive (which was supposed to be untouched, and carries my Windows98SE and Windows2000 dual boot system.

Basically it looks like this:

Channel-1
Master HD
-Windows98
-Windows2000
Slave HD
-WindowsXP

Channel-2
Master HD
-ubuntu

For some reason, when I did a BIOS update, it updated some HD controlling function that can allow the different hard drives above to be set as a virtual booting drive. Eg: Selecting MasterHD on channel one will only show 98/2000. Selecting SlaveHD on channel one will boot straight into XP. And MasterHD Channel two was suppposed to have ubuntu, but when GRUB came along, it wrote to the MasterHD of channel-1.

So basically I need to "undo" or "fix" what GRUB did to that drive and make it able to boot into 98/2000 again.

HELP! Thanks in advance![/QUOTE]
 so you can't boot into win98/win2k only? is there a cd that came with your window installs that allows you a recovery console to reset the MBR for your hdd? it may be a bit trickier with the multiple channels, though.

---

### Post by phend-one on 2005-06-18
Problem solved. It's not as complicated as I thought.

- Set the channel to the one you want to fix
- Get a floppy, Win98SE Bootdisk with fdisk.exe
- Go to the command prompt
- Type: fdisk /mbr
- Reboot

That should be the solution. Windows 2000 is a little glitchy right now, but nothing an install can't fix.

Looks like I need to do more reading before I install ubuntu half-heartedly.

---

