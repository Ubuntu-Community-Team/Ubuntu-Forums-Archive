---
title: "Windows 7 No Longer Booting after installing Ubuntu 13.10"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by Neil_Power on 2014-01-18
I have an Asus S46C laptop which I just flattened this evening. 

I started by installing Windows 7 64 bit to a partition on my 1TB SSD.

I then installed Ubuntu 13.10 on my 24GB SSD. 

Both OSes were installed EFI, I chose my SSD as the location of grub.
[SIZE=2]
I can boot into Ubuntu without issue but I am unable to boor into windows.

I completed the installation using the  [/SIZE][FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2][COLOR=#333333]"Installing Ubuntu Quickly and Easily via Trial and Error" section of this page [/COLOR][/SIZE][/FONT][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[SIZE=2][COLOR=#333333][FONT=Ubuntu]I ran Boot Repair as suggested and the URL it gave me is [http://paste.ubuntu.com/6777859](http://paste.ubuntu.com/6777859)
[/FONT][/COLOR][/SIZE][FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2][COLOR=#333333]I would really appreciate some help as I am uncertain how to proceed, thank-you.[/COLOR][/SIZE][/FONT]

---

### Post by Bucky Ball on 2014-01-19
Sounds odd, but what is in your sdc? If there is a disk in there, take it out and reboot, making sure your BIOS is set to boot from the correct drive (sda with the FAT EFI partition at the beginning).

---

### Post by Neil_Power on 2014-01-19
> **Bucky Ball said:**
> Sounds odd, but what is in your sdc? If there is a disk in there, take it out and reboot, making sure your BIOS is set to boot from the correct drive (sda with the FAT EFI partition at the beginning).

There is no disk in sdc. When I boot from the Windows boot loader in sda, I get the "Windows failed to start error" seen [here]("http://imgur.com/mVO59pe")

I installed using Windows 7 on a USB, Booting from the EFI on the USB gives me the same error.

---

### Post by oldfred on 2014-01-20
Which Windows entry are you using?

You have run the "buggy" UEFI rename function from Boot-Repair which is for those UEFI where vendor hard codes UEFI to only boot Windows. From UEFI menu choosing Windows actually boots grub. If you can boot from ubuntu entry in UEFI which also leads to grub undo the rename so you can boot Windows directly from UEFI menu. with the rename, then only the entry to boot bkpbootmgfw will actually boot Windows.

 Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Then set ubuntu as default in UEFI to boot to grub and in grub menu booting bootmgfw.efi will work. But you also then can directly boot Windows from UEFI menu which sometimes may be required if it needs chkdsk or other repairs.

---

