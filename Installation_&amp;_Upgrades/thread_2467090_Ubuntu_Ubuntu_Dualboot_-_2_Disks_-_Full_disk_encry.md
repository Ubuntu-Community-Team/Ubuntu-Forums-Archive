---
title: "Ubuntu Ubuntu Dualboot - 2 Disks - Full disk encryption"
date: 2021-09-15
forum: Installation &amp; Upgrades
---

### Post by froodproton on 2021-09-15
Hi!
I am trying and dying four days .... installing Ubuntu two times
- On a Lenovo Notebook (T470)
- On two hard disks (one nvme, one sata)
- With LUKS "full" disk encryption
- Using the graphical wizard

It doesn't ask me if grub should be installed, but there is ESP and a /boot partition as a result of the automatic partitioning. 
Whatever I do: The Lenovo starts up with the latest installed ubuntu. 

Info: In BIOS, there is the item ubuntu for each installation and after renaming it (analysis 2) there will be more added with the new names.
In grub menu, there is always just one entry. 

**1st analysis: **
In efibootmgr, both items have the same GUID --> point to the same disk. Explains why the latest starts only.  

**2nd analysis: **
I guessed that the second installation overwrites the grub entry for "ubuntu" and then, after the 1st installation, I changed the name in /etc/default/grub and update-grub
The same for the snd installation, after the installation, I have changed the name in /etc/default/grub and update-grub
In efibootmgr, the two items for the two ubuntu have different names, different GUIS, ok.
But there is a third one called "ubuntu" !! 
And in the Grub menu, there is just one with the name of the last/latest installation. 
Even if I efibootmgr change the order of boot devices, it doesn't matter. 

**3rd analysis / try**
running boot repair results in 
two efibootmgr items with the name "ubuntu" and the same GUID. Useless.  
> Boot0000* Ubuntu Main    HD(1,GPT,f7014beb-ce7f-42a8-9edd-185649d05abc,0x800,0x100000)/File(\EFI\ubuntumain\grubx64.efi)
Boot0001* Nightvision    HD(1,GPT,9e6a5af4-4f3a-4aa1-9237-712de8c57e80,0x800,0x100000)/File(\EFI\nightvision\grubx64.efi)
Boot0002* ubuntu    HD(1,GPT,f7014beb-ce7f-42a8-9edd-185649d05abc,0x800,0x100000)/File(\EFI\ubuntumain\shimx64.efi)
Boot0003* ubuntu    HD(1,GPT,f7014beb-ce7f-42a8-9edd-185649d05abc,0x800,0x100000)/File(\EFI\nightvision\shimx64.efi)


Is there something I can do? Is this scenario supported?

_Side notes:_
- Boot with UEFI is active in BIOS
- Secureboot is turned off


Cheers, Frood

---

### Post by oldfred on 2021-09-15
I have not tried it recently, but no.

I have changed distribution in grub to have unique name. Then sudo grub-install uses that name. You can see the various entries. They all boot the one Ubuntu using /EFI/ubuntu/grub.cfg. I also tried different names with efibootmgr.

It seems something is hard coded to use only  /EFI/ubuntu/grub.cfg. It used to be that there was not even a grub.cfg in the other distributor folders in the ESP. Once they added the grub.cfg, I thought it would work, but whatever is hard coded, does not use the grub in that folder.

```
[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for fred:  
BootCurrent: 0001 
Timeout: 1 seconds 
BootOrder: 0001,0003,0002,002C,002F,001C,0000,0025,0004,0031,0032,0033 
Boot0000* bionic1804    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\BIONIC1804\SHIMX64.EFI) 
Boot0001* ubuntu        HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\UBUNTU\SHIMX64.EFI) 
Boot0002* focal HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\FOCAL\SHIMX64.EFI) 
Boot0003* impish-k      HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\IMPISH-K\SHIMX64.EFI) 
Boot0004* debian        HD(1,GPT,8eab306c-97b9-4a07-a896-5ac4fb371311,0x800,0xf9dcd)/File(\EFI\DEBIAN\SHIMX64.EFI)


[/FONT]
```

I installed Debian just to see its grub.
It did let me install directly to my ESP on sdb, which Ubuntu's ubiquity will not. But have not experimented with multiple versions using Debian's grub.

I do have an ESP on sdb, and have Ubuntu installs in that ESP. Then I have two ubuntu entries with different GUIDs ( did not show any in above list of entries above).

Have you tried two ESPs, one on each drive?
And then give unique names to each.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
If you already have installs, you will need an ESP - efi system partition on both drives. 
Then update fstab with correct UUID for second ESP for install on second drive. And then reinstall grub as it will use ESP in fstab. If you have changed distributor also, it will then use that as name of entry in UEFI and folder in ESP.

---

### Post by TheFu on 2021-09-15
The automatic installer doesn't support dualboot.  That's a much more complex problem and has to be manually attacked.  It is beyond my skill, but Paddy has written a guide that many people use to setup encryption in non-standard ways.

Encryption is one of those things that has many, many, many, subtle aspects in order to provide the greatest possible security.  It is easy for experts in the field to make mistakes which completely undermine the security possible though drive encryption.  I assume I'd mess it up and end up with a less secure system if I didn't just go with the defaults.

Rather than dual boot, have you considered running the other OSes inside a virtual machine?  I do that all the time on encrypted storage.  The encryption can be either outside the VM or inside the VM. It is up to you. I've done both, but would probably go with the VM-host storage being encrypted, then all the VM-guest machines on the encrypted storage would be encrypted as well.

---

