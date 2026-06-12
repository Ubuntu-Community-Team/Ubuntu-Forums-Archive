---
title: "Dual boot on multiple hard drives"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by xwind on 2011-02-28
Hi, I just bought a new HDD and I wanted to play around with Ubuntu 10.10 on it until I'm comfortable enough to get rid of windows. So I want to dual-boot, for now.

So here I have HDD 1 with Windows 7. I began the installing Ubuntu on HDD 2. I chose to do manual partitioning ..not that I actually know what I'm doing but rather because I'm afraid that the auto install might mess with my windows MBR. In case the new drive dies within a couple months or I decide I'm not happy with Ubuntu, I'd like to be able to fall back to windows without much hassle.

This is how I did my partitioning:
/boot = 100 mb
/     = 20 gb
swap  = 8 gb
/home = 70 gb
freespace = the rest of the drive (1TB+)

For the bootloader I selected the /boot partition.
I then clicked on / then proceeded to install. Installation successful. Reboot time.

First time I rebooted, it loaded windows right away. So I went into my BIOS and changed the boot order to load HDD 2 first. After I rebooted again, instead of getting grub, I got a blinking cursor. I booted the liveCD, and I checked that grub is indeed installed in /boot, but after another reboot, blinking cursor again.

What am I doing wrong?

---

### Post by Quackers on 2011-02-28
I personally, would not have a /boot partition. But in any case, grub needs to be installed to the drive, rather than a partition, as such. If your Windows drive is recognised as /dev/sda, then your second drive is probably /dev/sdb (but may not be, check it in the installer (or gparted). Grub is normally installed to /dev/sdb (if that is your second hard drive) not /dev/sdb1, for instance.
I would re-install without the /boot partition, installing grub to /dev/sdb

---

### Post by Mark Phelps on 2011-03-01
> **xwind said:**
> ...In case the new drive dies within a couple months or I decide I'm not happy with Ubuntu, I'd like to be able to fall back to windows without much hassle.

Then ... you should have (1) disconnected the Win7 drive, (2) installed Ubuntu to the only connected drive, (3) reconnected the Win7 drive, (4) set to boot from the Ubuntu drive, (5) use sudo update-grub in Ubuntu to modify the GRUB menu.

Sounds like you installed GRUB to the MBR of your Win7 drive.  That's likely to cause problems booting back into Win7.

---

### Post by xwind on 2011-03-02
> **Quackers said:**
> I personally, would not have a /boot partition. But in any case, grub needs to be installed to the drive, rather than a partition, as such. If your Windows drive is recognised as /dev/sda, then your second drive is probably /dev/sdb (but may not be, check it in the installer (or gparted). Grub is normally installed to /dev/sdb (if that is your second hard drive) not /dev/sdb1, for instance.
I would re-install without the /boot partition, installing grub to /dev/sdb

Thanks!!! This fixed my problem. I reinstalled and set the bootloader to /dev/sdb instead of /dev/sdb1 and now I can boot into Ubuntu. So now, if I change my boot order to boot my old HDD first, it goes right into Windows, and if I have my new HDD boot first, then it goes into grub and I can choose either Ubuntu or Windows.

@Mark: I didn't get to try your recommendation, but I appreciate the help though, thanks!

---

