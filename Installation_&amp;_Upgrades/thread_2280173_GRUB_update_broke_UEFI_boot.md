---
title: "GRUB update broke UEFI boot"
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by kpatz on 2015-05-28
Last winter I built a new firewall box using an Intel Atom D2500CCE mini ITX motherboard.  When I installed Ubuntu Server 14.04.1 (later updated to 14.04.2), I enabled UEFI boot in the BIOS settings, and installed the OS to boot using grub-efi.  This worked great, through several updates, up until this morning.  I woke up early so I figured I'd check for updates (haven't done so in a month or so) and there were a bunch, so I installed them.  Well, Murphy's Law struck, and I made a mistake doing this on a morning before having to go to work.  The machine wouldn't boot afterward, and since it's my firewall/router, it's my most critical box.

So, I grabbed a spare monitor and keyboard and plugged them in, and found the machine was displaying a message along the lines of "no boot device found, hit any key to reboot".  I grabbed a Lubuntu USB stick I made and booted off of that, and tried reinstalling grub using the steps I used when I originally built the system (I had built it in a VM originally and then cloned it to the hardware).  Basically, I mounted the SSD partitions to /mnt (including the EFI partition to /mnt/boot/efi), mount --bind the /dev, /dev/pts, /sys, /proc and /run to the corresponding directories on /mnt, chroot to /mnt and run as root:

```

apt-get install --reinstall grub-efi
update-grub
grub-install /dev/sda

```

I did these steps and it still wouldn't boot.  Now maybe I botched a step as I was rushing, but I wanted to get the machine back up and running before I had to leave for work.  As a last-ditch attempt, I turned off UEFI in the BIOS (reverting to legacy boot), changed the EFI partition to a BIOS partition, commented out the /boot/efi line in /etc/fstab, uninstalled grub-efi and installed grub-pc, ran update-grub and grub-install /dev/sda, rebooted, and voila!  It boots now.

Anyway, has anyone else had UEFI booting break with the recent grub update?  Can I get UEFI boot working again?  When I have some more spare time and can afford the downtime, I may make another attempt to make UEFI work again.  It worked great until now.  I'm just wondering if there's an issue with the updated grub and UEFI.

---

### Post by oldfred on 2015-05-28
That sounds more like a UEFI error, not from grub.
But then UEFI was having issues with either the FAT32 or its own entries in UEFI.

I would liked to have seen Boot-Repair's summary report, but not sure if it would show anything now.
Some just after an install seem to have similar issues. Too bad we did not have time to fully review what was going on.

I only converted to UEFI with my Desktop last fall. Have not had any issues but have not updated for a couple of weeks. 

I do have both an 300MB efi partition and a 1MB bios_grub partition on all my gpt drives. And all new drives and larger flash drives are gpt. 
 May be better to create a bios_grub separately so you do not have to overwrite efi.

---

