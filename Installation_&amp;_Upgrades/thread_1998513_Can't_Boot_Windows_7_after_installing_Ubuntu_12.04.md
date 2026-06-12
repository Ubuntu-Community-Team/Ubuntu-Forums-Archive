---
title: "Can't Boot Windows 7 after installing Ubuntu 12.04"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by rohaan06 on 2012-06-06
[http://paste.ubuntu.com/1027874/](http://paste.ubuntu.com/1027874/)

Hey, i am literally going crazy, been up for hourse on end sitting at this computer but i cant find on the internet what to do. Basically i had windows 7, i installed ubuntu 12.04 alongside it, played with it then when i tried to go back to it, it just came with "ERROR 15 : file not found " and then proceeds to go into the GRUB4DOS menu which is utterly useless. Please someone help me, im going crazy over this. I know all the files of my windows 7 are there because i can acess them so i cant seem to see the problem :/ also before you suggest to put a recovery disc in my computer, i have tried but the bootloader just will not let me boot the windows 7 disc. Itll let me boot the ubuntu install disc but not windows... my bios is set to dvd to load first too, i just dont know whats going on....
EDIT: also, boot repair didnt do nothing hense why i posted the file above

---

### Post by oldfred on 2012-06-07
Error 15 is an old grub legacy error.

But you have gpt and efi which only works with grub2.

You seem to have two efi partitions which has to greatly confuse things. Only sda1 should be an efi partition. Windows is installed in sda3 do that should just be a data partition.

Was Windows installed in UEFI mode booting from the efi partition?

You installed Ubuntu in BIOS boot and I do not think you can have Windows in UEFI and Ubuntu in BIOS and boot (but I have not seen anyone try it either). 

Both Windows & Ubuntu have two boot choices from the UEFI menu and the install CD or USB. One should be UEFI or efi and the other BIOS, legacy or maybe AHCI mode.

So I think you have to change sda3 to a data partition. And then boot both Windows & Ubuntu and install efi boot loaders to the efi partitions.

You may want to look in these that Boot-Repair created as backups to see if the Windows efi boot loader is there.

You should end up with these in the efi partition.
find /boot/efi -name "*efi"
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi

---

### Post by carl4926 on 2012-06-07
This just reminded me of why I prefer Linux only installs.

I wonder if the OP actually has a proper windows DVD?

---

### Post by rohaan06 on 2012-06-07
> **oldfred said:**
> Error 15 is an old grub legacy error.

But you have gpt and efi which only works with grub2.

You seem to have two efi partitions which has to greatly confuse things. Only sda1 should be an efi partition. Windows is installed in sda3 do that should just be a data partition.

Was Windows installed in UEFI mode booting from the efi partition?

You installed Ubuntu in BIOS boot and I do not think you can have Windows in UEFI and Ubuntu in BIOS and boot (but I have not seen anyone try it either). 

Both Windows & Ubuntu have two boot choices from the UEFI menu and the install CD or USB. One should be UEFI or efi and the other BIOS, legacy or maybe AHCI mode.

So I think you have to change sda3 to a data partition. And then boot both Windows & Ubuntu and install efi boot loaders to the efi partitions.

You may want to look in these that Boot-Repair created as backups to see if the Windows efi boot loader is there.

You should end up with these in the efi partition.
find /boot/efi -name "*efi"
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi

Ok, so youve said all this buy how do I got about doing it? :P sorry, I'm just new to this side of computers and I'm really not sure what I'm doing... Thankyou though!

Also I just realized that the first EFI partition was remnants on an Apple Mac OSx install I did so I removed the partition.

---

### Post by darkod on 2012-06-07
It's a bit more complicated than that. Is your disk msdos or gpt? I know fdisk says it's gpt but that can be the backup gpt table also.

I am asking because win7 can work on gpt only if EFI boot is used. So you will not be able to make all of this work without EFI boot and the EFI system partition.

After you played around with the OSX you should have made the disk msdos table, and make sure it's msdos. If you tried windows tools they can sometimes delete the main gpt table but leave the backup table and this confuses linux.

If you keep using it as gpt windows7 can't work without the EFI boot, and making the dual boot work correctly is sometimes a challenge too. The EFI is still new and you need to investigate more for correct dual booting on it.

In any case, I think you don't need the /grldr files on sda3 because that's usually part of grub/grub4dos and that might be the thing messing it up for you. Usually you need only the win7 boot files on the windows partition, not the grldr.

---

### Post by oldfred on 2012-06-07
If this drive was from a Mac with Windows then you may have a hybrid msdos/gpt drive. Macs use gpt but install Windows in MBR(msdos) mode. Considered not very reliable and you have to be very careful to keep them in sync.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

And it that is the case, it may just be easier to start over with all new partitions in MBR mode. Windows only boots from gpt drives if in UEFI mode and only newer computers use UEFI. Apple has a older UEFI implementation which Windows still is in MBR mode.

You may be able to convert to MBR but will still have to make repairs to get things booting.

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

