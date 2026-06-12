---
title: "Installing dual-boot Natty Narwhal 11.04 on EFI capable systems"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by julester23 on 2011-04-28
I bought a Lenovo x120e which has EFI support (maybe others with E-350s have the same problem). After installing via USB disk, the system boots up to an Ubuntu Rescue screen and states "error: invalid arch independent ELF magic". I found a few posts of this problem, but didn't see any good answers. 

I'm guessing that Ubuntu installer assumed that I had EFI setup properly (which i did not because i'm pretty sure the default windows 7 install uses legacy MBR and there is no partition setup for EFI)

Here's what I did to fix the problem:

Assuming you are dual-booting with the default windows install and installed Natty to /dev/sda5 on your /dev/sda disk...

[LIST=1]
[*]Boot from your USB disk for Natty Narwhal
[*]mkdir /media/disk
[*]mount /dev/sda5 /media/disk
[*]grub-install --boot-directory=/media/disk /dev/sda
[*]reboot (you should now get a full grub, not just grub-rescue)
[*]commands to type at grub prompt (please note the partition names, they may differ from mine):
ls
[*]commands to type at grub prompt (TAB-completion is your friend):
set root=(hd0,msdos5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot   
[*]after bootup run (this will remove the EFI grub and install the MBR version):
sudo apt-get install grub-pc
[/LIST]
I know there is a way to avoid the manual process of typing in all the grub commands if you can get update-grub to run in a chrooted environment on your hard disk...but you have to mount /dev and maybe /proc.

I hope this helps someone!

---

### Post by hyphan on 2011-05-04
You bet that helped me, Thanks!

HP Elite 7200, Partition that first looks like an EFI partition is there, but after all it belongs to Win7 (ntfs). 
Natty-Installer used grub-efi, but nothing worked.

Just installing the grub-pc package and issuing another "grub-install /dev/sda" helped. It can be so easy, if you only knew before the hours of fiddling around..

If you use an USB Stick for installation, booting into the installation on HD can be done easier by editing the grub.cfg in /boot/grub on the stick. 
Or probably you can also boot the system from stick/CD, then mount the partitions below /mnt, and go there using chroot. Of course, not before you --bind mounted /dev, /proc, /sys.

Just to mention it: I also did another Natty install (Kubuntu to be exact) on another box, and again grub installation failed, for some other reason not yet known. In that case, a simple call to grub-install from within the installation helped. In terms of the boot system recognition / boot manager installation 11.04 seems not really mature yet.

---

### Post by ProNux on 2011-08-17
I have an almost similar hardware - Fujitsu PH521, AMD E-350 with Phoenix Secure Tiano BIOS & Win 7 HP 64-bit installed
I am not aware/never heard of this EFI so I just installed Natty on a separate partition via unetbootin (USB).  The install went fine.  After reboot, the grub did not show up and just boot directly into Windows 7.  Worst, I deleted the GPT partition (but I have an image backup).


Is this completely messed up?  I have read about creating a gpt partition and install boot loaders for each OS.  I'm stil new to this and may spend a week or so researching.

I restored the Windows partition and I can still boot but still no success of booting on Ubuntu after successfull install via USB.

Will the procedure above work for me (I cannot try now, I'm at work)?  I have a 64-bit Win7.  Or can anyone provide a direct instuction from the very start of dual booting Win7 & Ubuntu on a UEFI machine.

Thanks.

---

### Post by 905jay on 2011-09-16
> **julester23 said:**
> I bought a Lenovo x120e which has EFI support (maybe others with E-350s have the same problem). After installing via USB disk, the system boots up to an Ubuntu Rescue screen and states "error: invalid arch independent ELF magic". I found a few posts of this problem, but didn't see any good answers. 

I'm guessing that Ubuntu installer assumed that I had EFI setup properly (which i did not because i'm pretty sure the default windows 7 install uses legacy MBR and there is no partition setup for EFI)

Here's what I did to fix the problem:

Assuming you are dual-booting with the default windows install and installed Natty to /dev/sda5 on your /dev/sda disk...

[LIST=1]
[*]Boot from your USB disk for Natty Narwhal
[*]mkdir /media/disk
[*]mount /dev/sda5 /media/disk
[*]grub-install --boot-directory=/media/disk /dev/sda
[*]reboot (you should now get a full grub, not just grub-rescue)
[*]commands to type at grub prompt (please note the partition names, they may differ from mine):
ls
[*]commands to type at grub prompt (TAB-completion is your friend):
set root=(hd0,msdos5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot   
[*]after bootup run (this will remove the EFI grub and install the MBR version):
sudo apt-get install grub-pc
[/LIST]
I know there is a way to avoid the manual process of typing in all the grub commands if you can get update-grub to run in a chrooted environment on your hard disk...but you have to mount /dev and maybe /proc.

I hope this helps someone!


Sure as hell solved my issue.

Built an HTPC with the following componants:
AMD A6 3650 APU
Asus F1A75-M Pro MB
8 GB DDR3-1600 RAM
Thermaltake 600 PSU
4 2TB WD Black Drives
Mythbuntu 11.04 amd64(also tried xbmx [sucks for live tv, awesome for everything else])

I encountered some issues with ELF magic ("error: invalid arch independent ELF magic") so I brought out the Warlock :)

Anyways, issue resolved doing what was listed above, step-by-step. Thanks for the guide buddy!!

---

