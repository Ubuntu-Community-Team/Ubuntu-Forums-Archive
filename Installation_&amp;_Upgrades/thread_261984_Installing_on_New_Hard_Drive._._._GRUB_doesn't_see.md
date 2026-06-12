---
title: "Installing on New Hard Drive. . . GRUB doesn't see Windows"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by LordMaiku on 2006-09-21
Hi,

I finally decided to get into Linux a little more seriously, so I bought and installed a new hard drive for my main PC (Seagate, 80GB SataII). I have been  running Windows XP for a while on RAID 0, as configured by the nVidia RAID controller built in to my motherboard. I also have a third NTFS hard drive that stores backups.

On my first try, I installed Ubuntu from the 6.06 live CD on the new drive, with all other drives connected. After it rebooted, my system froze after displaying the device list. . . it didn't boot anything.

On my second try, I disconnected all but the drive for Ubuntu. I installed again, and when I rebooted, Ubuntu loaded correctly. This is good: at least I have a working computer.

The next step, and the one I need help with, is making the system dual-bootable. All I want is for GRUB to offer Ubuntu (default) and WinXP. How can I do this?

Thanks a million!

---

### Post by LordMaiku on 2006-09-21
I forgot to mention that it would be acceptible to use the Windows boot loader instead of GRUB. I've seen some info on how to do this. . . but I would need to be able to boot Windows to edit boot.ini. 

Assuming I am able to boot Windows, does anyone have a good tutorial for booting Ubuntu 6.06 from the Windows bootloader? Ubuntu will be on drive sdd (fourth sata). . . or maybe sdc (third sata) if the raided drives count as sda (any ideas which it will be?).

Thanks in advance. . .

---

