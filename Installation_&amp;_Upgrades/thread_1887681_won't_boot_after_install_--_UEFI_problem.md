---
title: "won't boot after install -- UEFI problem?"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2011-11-27
I just installed the most recent Ubuntu 64bit on a new homebuilt machine and the installation went fine but I can't boot to Ubuntu after restarting!

Some details: it's a new machine I built with my son, lots of RAM, Intel i5, MB is "MB ASROCK|Z68 EXTREME3 GEN3 1155 R", WD 1TB HDD, etc.  He wanted the Other Operating System for gaming, so we bought and installed that no problem.  Then we went to ubuntu.com and downloaded the most recent 64bit installation disk image; we had no blank disks around the house so instead we used some utility which ubuntu.com pointed us to in order to get a bootable USB stick with the disk image on it.

Restarted, got to the boot selection menu and booted from the USB stick.  Had the usual Ubuntu installation dialog, then it finished, we restarted... no GRUB menu, goes directly to Windoze.

Started again off the USB, this time I chose "try Ubuntu".  Ran Gparted and in fact the Windoze partition is shrunk and there is an ext4 partition.  (There's also some tiny partition at the beginning of the disk, I guess has the boot loader; this is all automatic choices from the Windoze install and the subsequent Ubuntu install and repartition.)  (Note the Windoze still continues to boot fine and to run.)

Now this new MB doesn't use BIOS... I believe.  It's the UEFI thing instead, I guess.  But I hear that new Linuxes can deal with this w/o problem, so what is the issue?  Do I have to set some weird booting parameter in the pre-boot menus off the MB (what I used to call the BIOS set-up, but I guess cannot be BIOS set-up if there is no more BIOS)?  Or manually install ... what, grub-efi?

Help!

---

### Post by dabl on 2011-11-27
I thought all UEFI implementations were going to include backward compatibility to MBR/BIOS booting.  I can't tell from the ASROCK specs for your board.  I would suggest looking in the BIOS for a switch to let it use a "BIOS Personality" and boot from the MBR.

---

### Post by bodhidharma on 2011-11-27
Yeah, I thought so too.  No obvious choice in the UEFI start-up screens, though.  Maybe I need to put a jumper on the MB itself....

Thanks for the suggestion, dabl.

---

### Post by oldfred on 2011-11-27
If you installed Windows with UEFI you also have gpt partitioning. Windows will not boot gpt partitioning with BIOS.

Best to fix UEFI if possible. Grub has some issues still with the UEFI boot process.

Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---

### Post by bodhidharma on 2011-11-28
OK, this is apparently a deep rabbit hole.  I've read a number of the threads you pointed to, and it seems there is a lot there.

It is unfortunate that this is one of those situations that the Linux community hasn't yet dealt with some very new technology in a completely painless and automatic way.  I remember when every new install involved days of painful work to get the wireless working ... now it is usually more or less automagic.  Not so the UEFI issue, I guess.

I can't tell if the MB has a pure BIOS fall-back.  There is nothing obvious in the manual (which can be found at [http://www.asrock.com/mb/manual.us.asp?Model=Z68%20Extreme3%20Gen3](http://www.asrock.com/mb/manual.us.asp?Model=Z68%20Extreme3%20Gen3)) although the word "legacy" does occur... to do with setting the SATA0 to "Compatible" "when you install a legacy OS".

Suppose I want to fall back entirely to BIOS (which I know well). Would the following work, do you think?
1) Set that "compatible" flag".
2) Completely reformat the hard drive.  (How, exactly?  And I assume that I would need to do this so the next step would not simply have Windoze re-installing into an UEFI setup again.)
3) Completely reinstall Windows in BIOS mode.  -- Anyone know how this works?  I wasn't in the room when the Windoze install happened already (made me too sick to my stomach), so I don't know if there was ever a choice about this.  I suppose there should be...?  Will it be in some code again, like the MB menus?  (This is Windoze 7 Home edition, by the way.)
4) Then do a regular Ubuntu install "along side the existing Windoze installation"... and it should all just work out of the box, with the GRUB menu coming up, etc.

Is that correct, do you think?

BTW, thanks for all this help!

---

### Post by oldfred on 2011-11-28
Gparted's default is MBR(msdos) partitioning. Not sure about Windows, but if Ubuntu detects a drive over 1TB it uses gpt, not sure how it know to use BIOS or UEFI. I use gpt with BIOS but have Windows on a separate MBR drive.

I now format all drives as gpt (no Windows) with both a efi partition of 300MiB and a 1MiB bios_grub partition. Only one or the other will ever be used. If drive is in MBR as it is now grub will use bios_grub. If I put drive in a UEFI system tomorrow then it will use the efi partition.

Windows 7 default install in MBR is a hidden 100MB boot/repair partition and a main (c:) install. Both are primary partitions. But if the NTFS partition is created in advance with the boot flag, it will install in one partition. There have been some reports of NTFS formated by gparted not working with Windows 7 installer, so you may have to reformat in Windows and reset boot flag before the install.

Some of these bugs they are working on and others do not have enough users reporting issues that they think they are important. I find most are like you and just give up, so no bug report is filed.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

