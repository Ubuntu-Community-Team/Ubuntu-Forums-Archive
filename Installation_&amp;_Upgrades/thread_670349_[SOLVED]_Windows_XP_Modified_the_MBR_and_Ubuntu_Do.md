---
title: "[SOLVED] Windows XP Modified the MBR and Ubuntu Doesn't Boot"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by xanders on 2008-01-17
Hi all, I have my laptop with Ubuntu 7.10 (Gutsy Gibbon) using GRUB as a boot loader for Ubuntu and Windows XP each one has their own drive, for some reason i have to delete the Windows XP partition and make a new installation and now windows Modified the MBR with the NTLDR and now my Ubuntu partition doesn't boot. There's a way to fix this without Reinstalling Ubuntu? :confused: . Thank You.

---

### Post by PmDematagoda on 2008-01-17
The best tool(in my opinion) to use in order to restore GRUB to the MBR is [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download").

Burn the ISO to a CD in Windows, and then boot the PC using that CD, the rest of the process is easy:).

---

### Post by b0rka7a on 2008-01-17
Windoze is BAD ! :) So you are using two hard drives ? If so, I guess you could open your laptop and move the jumper of the Win HDD from Master to Slave and move the jumper of the Ubuntu HDD from Slave to Master (I'm just guessing, not sure!!). At least I would do that, but that's my work so it's not any problem for me ((:
(sorry if i have spelling mistakes :))

---

### Post by itix on 2008-01-17
! I don't use windows and dual boot, but if I'll ever do, I'll stick to the super grub disc. Works like a charm.

---

### Post by RockHaxor on 2008-01-17
Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.
```
sudo grub
root (hd0,0)
setup (hd0)
exit
```

Reboot (removing the livecd), and your boot menu should be back.

---

### Post by sandysandy on 2008-01-18
> **xanders said:**
> Hi all, I have my laptop with Ubuntu 7.10 (Gutsy Gibbon) using GRUB as a boot loader for Ubuntu and Windows XP each one has their own drive, for some reason i have to delete the Windows XP partition and make a new installation and now windows Modified the MBR with the NTLDR and now my Ubuntu partition doesn't boot. There's a way to fix this without Reinstalling Ubuntu? :confused: . Thank You.

in such a situation u may consider booting using ubuntu live cd

use code  [COLOR="Blue"]sudo fdisk -lu[/COLOR] in terminal and see output to see which partition is windows and which is ubuntu. (NTFS partition will be windows and ext3 will be ubuntu)

Then mount partition using code
[COLOR="Blue"]sudo mount -t ext3 /dev/sda1 /mnt/ubuntu[/COLOR]

Then use following code

 [COLOR="Blue"]gksudo gedit /boot/grub/menu.lst[/COLOR] 


this will open ur menu.lst file.

in menu.lst file check that the ubuntu partition number is set correctly. 

eg 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR="Blue"]root		(hd0,5)[/COLOR]  [COLOR="Red"]<---CHECK THIS [/COLOR]
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fe8f4e4-bb66-4c5b-b33c-7a24d4f1cdd8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


regards

---

### Post by shakyone on 2008-01-18
If you really have a laptop with two hard drives then I would recommend b0rka7a's recommendation.  I dual boot using two hard drives on my home computer, I just uninstalled the Windows drive during the Ubuntu install.  Then I re-connected with the Windows master boot record intact on its drive, in the slave position, and I put the Ubuntu drive in the master position, then I edited the GRUB menu.lst file in accordance with Confused57's instructions at:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

I used this as my baseline method, it was fantastic.  Now I need to learn how to do it with two SATA drives, as that will be my next computer.

I have not heard of a laptop with two hard drives though.  So if you actually have a laptop with one hard drive with two partitions, you will probably want to follow the other recommendations like using SuperGRUB etc...

---

### Post by xanders on 2008-01-21
> **PmDematagoda said:**
> The best tool(in my opinion) to use in order to restore GRUB to the MBR is [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download").

Burn the ISO to a CD in Windows, and then boot the PC using that CD, the rest of the process is easy:).

Thanks the Super Grub Works like a Charm. :D and now :lolflag: Ubuntu is back  [-o< i Use windows because of Visual Studio .NET that the only reason that i have Windows XP on Dual boot. and Thank You Guys for all the replays.

---

