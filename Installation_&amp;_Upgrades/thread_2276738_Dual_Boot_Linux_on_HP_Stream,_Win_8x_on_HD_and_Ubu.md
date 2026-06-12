---
title: "Dual Boot Linux on HP Stream, Win 8x on HD and Ubuntu on SD Card ?"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by Jean-Francois_Bour on 2015-05-04
Can I dual boot on my HP stream with Ubuntu on a  SD Card ? 


- Windows 8.x on the built in 32 Gig RAM  Hard drive
- Ubuntu on a 64 gig SDCard


I did installed Linux Mint last version on the 64 SDCard but during the installation
NOTE : I would prefer UBUNTU as all my home stations are Ubuntu and I am used to it...  but this test I did was easier with mint


- I was not offered Windows compatibility ( coexistence ) during installation
( manuallycreated the root, home and swap partions on the 64 gig MemoryCard)


when done, I rebooted and no boot menu... Only going to Windows 


If this can be done, this would be my prefered scenario


If you tell me some of the Linux partition need to be on the same HD as Windows, and Root and Home partition on the SD card, I could deal with that


JF

---

### Post by ubfan1 on 2015-05-04
Assuming you can boot from the SD card (some machines cannot, so you'd have to use a USB reader since USB booting is more common), you should set it up in UEFI mode like Windows.  This means setting up an EFI partition with a 300M FAT filesystem, and the boot flag.  You should be able to specify the SD's EFI partition as the location for the bootloader, and a successful install will put the ubuntu bootloaders into /EFI/ubuntu.  The files will be grubx64.efi, shimx64.efi, and the grub.cfg stub file which copies in the maintained grub.cfg file from the install's /boot/grub.  Common errors are for the bootloaders to get put onto the hard disk's EFI partition.  If that happens, you can just copy them over to the SD's EFI, they are just files.  Now that setup is just like the hard disk's,but it may not work for removable media, which has its own default bootloader, which does not need a nvram entry beyond the general SD (or USB) boot.  Removable media's default bootloader is in /EFI/Boot/bootx64.efi.  If that directory does not exist on the SD's EFI, make it, and copy shimx64.efi there, renaming it to bootx64.efi.  Also copy grubx64.efi into that directory.  The grub.cfg file may be left in the /EFI/ubuntu directory.  Specify the SD/USB to boot, and grub should run, giving you a menu of boot choices.  Further reading:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by Jean-Francois_Bour on 2015-05-05
Tks  a lot [[COLOR=#000000]ubfan1[/COLOR]]("http://ubuntuforums.org/member.php?u=1256996")[COLOR=#000000]  for taking time to write a complete answer... I will read it a few times and try to apply it
JF

[/COLOR]

---

