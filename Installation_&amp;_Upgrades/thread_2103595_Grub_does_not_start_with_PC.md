---
title: "Grub does not start with PC"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2013-01-10
Hi there, 

I installed ubuntu 12.04 on a computer that had windows by default. I partitioned the disk to leave windows on (sic) and the installation went ok

But when I restarted the computer I found out that it starts windows by default...the GRUB screen does not appear at any time

The only way to start linux is to keep the USB drive (I used for the installation) plugged to the computer and press Esc, in which case the GRUB screen appears...

I cannot even re-install ubuntu from that USB drive....any chance that I can get GRUB screen from the beginning as it should be?

thanks in advance

---

### Post by Bufeu on 2013-01-10
> **abelito8 said:**
> Hi there, 

I installed ubuntu 12.04 on a computer that had windows by default. I partitioned the disk to leave windows on (sic) and the installation went ok

But when I restarted the computer I found out that it starts windows by default...the GRUB screen does not appear at any time

The only way to start linux is to keep the USB drive (I used for the installation) plugged to the computer and press Esc, in which case the GRUB screen appears...

I cannot even re-install ubuntu from that USB drive....any chance that I can get GRUB screen from the beginning as it should be?

thanks in advanceTake a look at this [http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot/106706#106706](http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot/106706#106706) and this [http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot/88868#88868](http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot/88868#88868).

---

### Post by darkod on 2013-01-10
It installed grub2 to the usb stick. Boot it once with the stick plugged in, open terminal and execute:
sudo grub-install /dev/sda

That should install it onto the MBR of the hdd provided the hdd is /dev/sda. Try booting without the stick after that.

If you want to check whether the hdd is /dev/sda before executing the above command, you can do it with:
sudo fdisk -l (that's small L)

---

### Post by abelito8 on 2013-01-13
I am afraid I have found out what happened...
if I enter the bios I am given only two boot options

1. windows boot loader
2. DVD

In all old versions of bios the main option to start was HDD... not windows boot loader, it seems microsoft has inserted this option in the bios to make impossible to use anything else than windows...anyone who has solved this?

---

### Post by darkod on 2013-01-13
Are you talking about UEFI boot?

If your computer uses the old standard legacy boot, it has to give you an option for the hdd as boot device.

In the newer uefi boards, you might get a bootloader menu little bit different than before. Personally I don't use uefi, so I don't know much about it.

Boot-repair can help with menu boot issues, you can try running it from live mode. You can use it only to create the bootinfo so you can see what is where, or you can also use its recommended repair function.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

