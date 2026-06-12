---
title: "[long] Problem to install kubuntu 7.04 with Windows Vista in dual boot"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by marcomangiante on 2007-08-12
Hello,

I tried to install kubuntu 7.04 in dual boot with windows vista, but the installation failed. My problem is related to the fact that I want to maintain the vista boot loader and insert in it the kubuntu entry. 
To do this I have to change where the grub bootloader install itself, so not in mbr but first boot sector of linux partition.
After followed all the steps to install kubuntu, I arrived at the final install window where you find the summary of all the option you choose, and in that window there is a Advanced button. I clicked on it, and tried to instruct the installation program to install grub in the first boot sector of linu partition (in my case, hda2), but this filed because at installation time when the program try to install grub, the program fail because no correct path. For path, I used /dev/hda2 and also (hd0,1), but no result.
So, because all the system is installed, I tried to install grub manually.
With the live cd, I created a menu.lst file and copied it in the /boot/grub/ directory (that on the physical disk, not that created every time you run the live cd).
I modified the entry in menu.lst so it poits to (hd0,1) and then used grub command find on this forum, i.e.: 

root (hd0,1)
setup (hd0,1)

Sincerely, due to failed installation, I don't know if all grub files are present and also I dont' know if root(hd0,1) have worked.

However, after insert the entry for linux in the vista boot loader, I tried to load kububtu and grub seems to work, but I received this message:

[     30.019449] Kernel panic - not syncing: VFS: Unable to mount root fs unknow-block(0,0)
[     30.019523]

I also tried to launch the recovery mode from grub and obtained an infinite list of this type

[    xx.xxxxxx] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly

where x are numbers.

So, in your opinion, it is possible to repair the installation? Notice that when I received the grub error at 94% of installation, the setup stopped to work, so I never do the first launch of linux, so maybe the installation is not complete. If not and I must to reinstall, how to say to grub to install to first boot sector of kubuntu partition?

Thanks to all people that give me an help.

--
Regards,

Marco Mangiante

---

