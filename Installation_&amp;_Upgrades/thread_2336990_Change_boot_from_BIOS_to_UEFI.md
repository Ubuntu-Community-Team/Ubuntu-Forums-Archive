---
title: "Change boot from BIOS to UEFI"
date: 2016-09-13
forum: Installation &amp; Upgrades
---

### Post by alvaromaceda on 2016-09-13
My computer died, but I would like to keep my Ubuntu Server installation if possible.

I purchased a MSI cubi N and changed the HDD to the new computer. My old computer booted with BIOS, and the new one with EFI. A live CD boots ok, but my old drive did not boot, of course.

I installed and executed boot-repair, but it failed. It told me:
> The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, >200Mo, start of the disk}, EFI flag). Do you want to continue?

I continued, but the hard drive was unable to boot. Here is the pastebin:
[http://paste2.org/GKDHs4n0](http://paste2.org/GKDHs4n0)

I changed the partition table to GPT and tried again. It showed the same message as before. I continued, but didn't work:
[http://paste2.org/k8EcwF5J](http://paste2.org/k8EcwF5J)

After that, I moved all my data with gparted to the right, and created a new partition at the start of the disk as it asked. The next run, it told me:
> GPT Detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again. 


So I created a partition at the end of the disk. Now, the message was the first one. I continued, but it didn't worked. Here is the pastebin:
[http://paste2.org/WwPCXHJf](http://paste2.org/WwPCXHJf)

This is the partition table I currently have:
```
ubuntu-mate@ubuntu-mate:~$ sudo sfdisk -l /dev/sda
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 180DF111-D5EE-4D4E-92E8-CDD8986A4D97

Device          Start        End    Sectors   Size Type
/dev/sda1      307200 1947764735 1947457536 928.6G Linux filesystem
/dev/sda2        2048     307199     305152   149M EFI System
/dev/sda3  1953519616 1953523711       4096     2M EFI System
/dev/sda5  1947764736 1953519615    5754880   2.8G Linux swap

Partition table entries are not in disk order.
```

I'm still trying to make sense on how EFI and grub2 work, but there are still a lot of holes in my understanding and I would like to have my server online... Could somebody give me a clue of what I should do?

---

### Post by oldfred on 2016-09-13
UEFI uses gpt as its standard partitioning. But can work with MBR(msdos) as live installer is MBR.

Grub has two versions, grub-pc for BIOS boot and grub-efi-amd64 for UEFI boot.

With gpt and Ubuntu you can boot in either BIOS or UEFI. But with BIOS boot you must have the 1 or 2MB unformatted partition with the bios_grub flag. And with UEFI you must have a 100 to 500MB FAT32 formatted partition (ESP - efi system partition) with the boot flag. If using gdisk the ESP is flagged with code ef00 and bios_grub with ef02. With gpt the actual internal code is a very long GUID that is used to know partition type.

You should only have one ESP per device, you are showing two, sda2 & sda3. Change sda3 to unformatted and change flag from boot to bios_grub if using gparted or parted.

I started using gpt with BIOS with 10.10, and when systems started to be UEFI, I partitioned all new or totally reformatted drives to gpt with both the ESP & bios_grub. Then able to use BIOS to boot, but move drive to newer UEFI system and not have to totally reformat at that time.

How you boot install media UEFI or BIOS is then how it installs. Or you can use Boot-Repair (or manually) reinstall grub version for UEFI or BIOS if drive is gpt. If drive was MBR(msdos) you should only boot with BIOS even though it may be possible to use UEFI.

---

### Post by alvaromaceda on 2016-09-14
Thanks for the information, I'll test again as soon as I can. 
I believe the problem is that my new computer can't boot with bios but in the old OS I had installed grub, not grub-efi. I'll try to install the bootloader by hand and see what happens.

---

### Post by oldfred on 2016-09-14
If old install is BIOS/MBR, then you in UEFI must turn off Secure boot. You may have to turn on CSM/Legacy/BIOS setting or several other settings also, like USB port boot.

---

### Post by alvaromaceda on 2016-09-16
Now it's working. 

It seems that my new computer does not work with BIOS, I didn't found it anywhere in its configuration. So that's what I did:


[LIST=1]
[*]With gparted, I removed the bios_grub flag from the last partition (/dev/sda5) 
[*]Added an esp flag to the first partition (/dev/sda2) 
[*]And then I installed grub-efi and added it by hand:
[LIST]
[*]chroot the old system:
[LIST]
[*]mount /dev/sda1 /mnt --> data partition 
[*]mkdir /mnt/boot/efi 
[*]mount /dev/sda5 /mnt/boot/efi -> fat32 efi partition 
[*]for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done 
[*]sudo chroot /mnt 
[/LIST]
  
[*]Install grub-efi:
[LIST]
[*]apt-get install --reinstall grub-efi 
[*]grub-install /dev/sda 
[*]update-grub 
[/LIST]
  
[/LIST]
  
[/LIST]

And done, it's boots ok!
Thank you very much for your help.[INDENT]
[/INDENT]

---

