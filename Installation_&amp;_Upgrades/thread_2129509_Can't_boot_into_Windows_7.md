---
title: "Can't boot into Windows 7"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by ohanll1 on 2013-03-26
I recently deleted a partition which I thought was just a linux mint which didn't install correctly. However, now I can't boot into Windows 7 from GRUB for whatever reason. 
I can get into ubuntu but that's pretty much it.
I tried to use a Windows 7 boot USB that I made with unetbootin but whenever I boot from it, it only shows the option "default" and I can't do anything from there.

I've read on some threads that you should modify the syslinux.cfg but mine doesn't seem to be the same as what most people say.
This is my syslinux.cfg:

```

default menu.c32
prompt 0
menu title UNetbootin
timeout 100


label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit 

```

---

### Post by fantab on 2013-03-26
So did you delete your Windows Partition? Was this deleted partition the first partition of your bootable HDD? 

Post the [Boot Info Script]("http://bootinfoscript.sourceforge.net/") here. Put the script on [pastebin]("http://pastebin.com/") and just post the link here.

Meanwhile, when you've booted Ubuntu try to run:

```
$ sudo update-grub
```

After running the above command, check to see if GRUB sees your Windows...

---

### Post by ohanll1 on 2013-03-26
I have two HDDs. One HDD (1TB) is for my Windows 7. The other HDD is for ubuntu and a linux swap and the partition I deleted :/

[http://www.pastebin.com/Za7KtkMt](http://www.pastebin.com/Za7KtkMt) 

sudo update-grub doesn't do anything to my GRUB menu. It says Windows 7 (loader) is an option in grub.cfg but it doesn't show up in GRUBs menu when I boot.

---

### Post by darkod on 2013-03-26
Are you using uefi boot or legacy boot?

fdisk reports sdb2 as EFI System Partition which doesn't seem to be true since the partition is ext4 and that's the ubuntu partition.

If you can, i suggest you go into BIOS and disable the uefi boot since it can confuse things. You also might need to purge and reinstall grub2 since I don't see /boot/grub/core.img for your 12.10 installation. I think you might be actually booting Backtrack grub, and not Ubuntu grub.

---

### Post by ohanll1 on 2013-03-26
I'm using UEFI and Legacy boot. Should I only select Legacy?

How do I purge and reinstall grub2?

---

### Post by darkod on 2013-03-26
I would set it to legacy only, because if sometimes you boot the cd in uefi mode it will install the OS in uefi mode, and then you will have a problem.

To purge, boot your ubuntu 12.10 and in terminal do:
```
sudo apt-get remove --purge grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```

Make sure in bios you are booting sda as the first option. Reboot and it should be OK.

---

### Post by ohanll1 on 2013-03-26
I'm doing sudo apt-get install grub-pc right now. Do I install it on sda or sdb? sda is my main HDD which I use for Windows 7 and sdb is for ubuntu.

---

### Post by darkod on 2013-03-26
I know but since sdb has gpt table, grub2 will not install correctly there. It needs a small partition that you don't have, although it seems you have space to create one if you want to.

On sda you have the grub from BT anyway, there is no windows bootloader now. You can install it on /dev/sda and see if everything works, later you can change to /dev/sdb.

---

### Post by darkod on 2013-03-26
If you prefer sdb, don't reboot and don't install it on sda. Let me know and I can give you some commands to run. If you want to do that, post the output of:
```
sudo parted -l (small L)
```

---

### Post by ohanll1 on 2013-03-26
Whichever is my best option. I'd like to have my main hard drive for Windows 7 only but if that's too complicated then I don't mind.
What do you suggest?

---

### Post by darkod on 2013-03-26
I suggest you do it now as I suggested, install grub on /dev/sda. If everything works, later you can install it on /dev/sdb too and put windows bootloader on /dev/sda.

The bootloaders don't matter much, you still need to use grub to boot because windows bootloader can't boot linux. Whether grub is on sda or sdb doesn't make much difference.

---

### Post by ohanll1 on 2013-03-26
[COLOR=#000000]:Ignore this reply, I double posted:[/COLOR]

---

### Post by darkod on 2013-03-26
The disk will still have windows, you are not changing the OS. I have to go offline for few hours now, if you want to install on sdb, post the result of the parted command I posted and I'll give you other commands when I can.

---

### Post by ohanll1 on 2013-03-26
[COLOR=#000000]I did it! Thanks so much Darko. Any equivalent of props on this forum?[/COLOR]

---

### Post by fantab on 2013-03-26
If there is an option to reinstall then I'd suggest you reinstall Ubuntu. If you have any DATA to rescue then do so. Boot with the LiveCD/USB and use GPARTED to delete all the partitions on /dev/sdb and then Delete Partition Table.

Recreate Partition Table as DOS and partition your HDD the way you like and reinstall Ubuntu. Only this time install Grub on /dev/sdb. (You MUST change the HDD boot order in the BIOS later to boot /dev/sdb first). 
After partitioning your HDD use [fixparts]("http://www.rodsbooks.com/fixparts/") to ensure that you don't have any GPT leftovers. 

You can also fix your Windows if you have Windows install Disk or Win Repair Disk: [Read Here]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html"). So when/if you select /dev/sda from BIOS to boot first only Windows will boot as it does without Grub.

---

### Post by oldfred on 2013-03-26
I would keep gpt on sdb, it has some advantages. Its main disadvantage is that Windows will only boot from gpt with UEFI.

But as Darko has mentioned you need a bios_grub partition for grub to correctly install in sdb. It only needs to be 1MB and is unformatted space.

       GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)


 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 

Unless booting with UEFI, you should not have an efi partition. Use gparted to remove boot flag.
Parted & gparted use the boot flag with gpt to define the efi partition. That somewhat confused users that in BIOS/MBR the boot flag was the Windows partition to boot from. With UEFI the efi partition is always the boot partition and you can only have one efi partition per drive.

---

### Post by darkod on 2013-03-26
If you want us to help with creating the small partition you need for grub2, post the output of this:
```
sudo parted /dev/sdb unit MiB print
```

---

