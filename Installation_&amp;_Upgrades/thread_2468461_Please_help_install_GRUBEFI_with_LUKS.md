---
title: "Please help install GRUB/EFI with LUKS"
date: 2021-10-30
forum: Installation &amp; Upgrades
---

### Post by alekksander on 2021-10-30
Hello. After updating mesa, my X failed to display anything. I decided to fix it from usb stick by reverting to previous version, but i though that since i'm already messing with usb sticks i might as well install there a standalone system so i can experiment on in the future. I tried to install ubuntu minimal (with de) on usb stick and it messed up  GRUB on my ssd. Next time i'm gonna use .img instead, but to the point... Now i'm unable to boot my system at all and i can see is a dashboard from grub command. Tried to fix it, but i probably done more damage than previously, so i whipped this partition and now i need to setup GRUB there properly to boot into my system.
This computer has one internal ssd with two partitions - one "nvme0n1p1" fat32 with flags: boot and esp; second LUKS encrypted "nvme0n1p2" without any flags.

I logged in with live usb, and here is what i've already tried:


sudo cryptsetup luksOpen /dev/nvme0n1p2 p2
sudo mount /dev/mapper/p2 /mnt
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /sys/firmware/efi/efivars /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt

apt install grub-efi[FONT=monospace]
[/FONT]
grub-install /boot/efi
```
[FONT=monospace][COLOR=#000000]Installing for x86_64-efi platform. [/COLOR]
Installation finished. No error reported.[/FONT]
```

but no luck. tried to look into efibootmgr, and it shows:

```
[FONT=monospace][COLOR=#000000]BootCurrent: 0006 [/COLOR]
Timeout: 0 seconds 
BootOrder: 0000,0005,0004,0006,0007,0001,0003,0002 
Boot0000* grub 
Boot0001  UEFI OS 
Boot0002  Hard Drive 
Boot0003  UEFI: Built-in EFI Shell 
Boot0004* ubuntu 
Boot0005* ubuntu 
Boot0006* UEFI: KingstonDataTraveler 3.0 
Boot0007* UEFI: KingstonDataTraveler 3.0, Partition 2
[/FONT]
```

i really lack knowledge, but it seems that perhaps something is wrong with this list?

maybe there are more grub/efi files than needed and can be deleted? but most importantly, how do i boot my nvme0n1p2?
 please, can someone help?

---

### Post by oldfred on 2021-10-30
Ubuntu Ubiquity installer only installs grub boot loader to first drive. 
And install to second or external drive then does not have grub on it, even if that is what you want. 
Now multiple workarounds.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 


You should be able to fix your boot, just by editing /EFI/ubuntu/grub.cfg in ESP - efi system partition which is a three line configfile type grub entry that refers to your full grub in your install. Do not know LVM & encryption, but if separate /boot would expect entry to refer to the grub in /boot. 

Your chroot & full reinstall of grub should have fixed it. As that creates new or overwrites ubuntu entry in UEFI and creates/replaces grub.cfg in ESP.

Better to see full UEFI entris to see which ESP it is using.It uses GUID/partUUID to know which ESP to look for boot files.
sudo efibootmgr -v
Compare partUUID to efibootmgr details:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

Also look at /EFI/ubuntu/grub.cfg in ESP to see what UUID & partition it is using to find full grub.cfg. Maybe because it is encrypted it needs more settings, but I do not know LVM nor encryption.

You may want to do this first, and then may be able to add lvm2 and cryptsetup. If you then mount encrypted internal drive and run sudo update-grub it should find your internal isntall.
For your external drive and a new install, you need to partition in advance to be sure it has an ESP and use one of the work arounds in the bug report.
If install is otherwise complete, you can just shrink any partition by 100MB and make it FAT32 with boot,esp flags. Then edit fstab on external drive to have that UUID, so if grub updates it uses correct ESP. You can copy /EFI/Boot &  /EFI/ubuntu folders from internal drive to external drive. Both folders required as external drives only boot from /EFI/Boot/bootx64.efi, but a full install needs the /EFI/ubuntu/grub.cfg file also.

---

### Post by alekksander on 2021-10-30
nothing that i have tried so far works. it's second day i'm struggling with this. i think i'm just gonna backup home directory and setup new system. anyhow thanks for fast reply!

---

