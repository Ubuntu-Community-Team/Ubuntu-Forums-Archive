---
title: "Live USB doesn't boot"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by Phrost on 2013-12-01
I have a new PC.. Windows 8 with UEFI. I disabled secureboot and fastboot.. and got Linux Mint to load.. eventually it installed ok but I had a lot of trouble getting the nvidia drivers to work, so I just deleted the whole partition and went back to Windows. Today, I figured I'd give Ubuntu a shot. Well, after trying 3 seperate USB applications (unetbootin, lili, and the one recommended by Ubuntu) I can't get the Live USB to load at all.. I open the boot menu and select USB and then it goes straight to Windows. Any ideas?

---

### Post by sudodus on 2013-12-03
We know too little about your computer to be able to help. Please specify

- brand name and model
- graphics chip/card, which nvidia model (some are easier, some harder to tweak)
- wifi chip/card

and also, let us know which version of Ubuntu you are trying: 12.04 LTS, 13.10 or some other version.

Without knowing more, I can suggest that you try some boot option. Start with ***nomodeset*** according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by keller.ee on 2013-12-03
Did you install linux originally using a CD?  I have a relatively recent Gigabyte motherboard that refuses to boot from USB.  I found out later that this was a known issue and that everyone that has the board has issues with booting it.  I was never able to boot from USB, I had to dig out a CD drive.

---

### Post by bschilke.biz on 2013-12-03
I have been using a xubuntu live iso on usb and I think it got screwed up when settings got saved to the stick one of the times I was running from it.  But I found removing the 'quiet splash' flag and the '--persistent' flag allowed me to see what was happening and allowed the boot or install finish.

---

### Post by fantab on 2013-12-03
> **Phrost said:**
> I have a new PC.. Windows 8 with UEFI. I disabled secureboot and fastboot.. and got Linux Mint to load.. eventually it installed ok but I had a lot of trouble getting the nvidia drivers to work, so I just deleted the whole partition and went back to Windows. Today, I figured I'd give Ubuntu a shot. Well, after trying 3 seperate USB applications (unetbootin, lili, and the one recommended by Ubuntu) I can't get the Live USB to load at all.. I open the boot menu and select USB and then it goes straight to Windows. Any ideas?

Post more info about your 'new PC', as 'sudodus' asks.

Have you [disabled 'FastStartup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows8?

When you "open the boot menu and select USB", are there more options for USB, like 'USB - HDD' etc. If there are then choose USB-HDD. 
Your UEFI is booting unable to boot from USB, check the UEFI/BIOS again and see if USB booting is enabled... 

Try another USB drive, just rule out any fault with the USB drive itself. 
When you Burn as .iso on USB, generally some GPT data is left behind when USB drive is not formatted properly, before Burning another .iso. This can render USB-linux unbootable.
I have faced this issue. The solution is to use [FIXPARTS]("http://www.rodsbooks.com/fixparts/") on the USB drive and 'create a new partition' table with GParted, create new partition and format it as FAT32. Then 'burn' the .iso on it.

---

### Post by Tweak42 on 2013-12-28
Adding here a solution that worked for me when trying to usb boot my Gigabyte 78LMT-USB3 board.  Apparently the picky gigabyte boards like whatever the voodoo magic the HP USB format tool does to USB drives.  Without it my gigabyte motherboard would not show bootable USB drives in the F12 -> Hard drive+ menu.  These were usb bootable drives that worked fine on 2 other computer systems.

[LIST=1]
[*]Install HP USB Disk Storage Format Tool (I used a XP install in a VirtualBox)
[*]Format your USB drive using the HP Tool and direct it to Windows 98 Startup Files
[*]Use Unetbootin to write your linux iso file to the usb drive.
[*]
[/LIST]

I found the explained post in detail here:
[https://bitcointalk.org/index.php?topic=90858.0](https://bitcointalk.org/index.php?topic=90858.0)

---

