---
title: "Ubuntu will not boot on Samsung Ativ Book 9 Plus"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by colin-schneider1996 on 2014-12-15
hey everyone, 
I have Samsung Ativ Boook 9 Plus, and i tried to install Ubuntu 14.10, I could boot from my USB-Stick, then i tried to install Ubuntu. But it wont Boot. 
The last thing i have done is, that i run Boot Repair. Now i have this text from Boot Repair. 

[http://paste.ubuntu.com/9530891/](http://paste.ubuntu.com/9530891/)

Pls can anyone help me?

---

### Post by oldfred on 2014-12-15
The sda1 is your efi partition for UEFI boot, but is showing as a data partition. You need to use gparted and right click on partition and add boot flag.

Boot-Repair says you have secure boot on. Better to have it off. You do show two ubuntu entries, one should work with secure boot on as it uses shim and both should work with secure boot off.

Not sure if Samsung is like many of the other vendors in modifying UEFI to only boot a "Windows" entry. If so a work around is required. Since only Ubuntu installed, best work around is to rename the ubuntu entry using shim to boot to Windows. UEFI thinks it boots Windows and actually boots shim (grub).

       Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.

 Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

If still not booting, use efibootmgr to rename the shim ubuntu entry to Windows. Then boot from UEFI boot menu the Windows entry. You have to boot Ubuntu live installer in UEFI mode to have efibootmgr.

      
 
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

       [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

To see UEFI boot entries:
sudo efibootmgr -v

---

### Post by colin-schneider1996 on 2014-12-15
I Have 2 new Boots. One named Windows Boot Manager and one named Windows. But in my UEFI i can only select USB.

---

### Post by oldfred on 2014-12-15
Do you have secure boot on, or some other UEFI setting?
You actually should be able to select the Windows Boot Manager & Boot to grub menu or straight to Ubuntu since only one install.

One of the linked threads talks about a boot password. Some systems require you to set a UEFI password to change any settings. But never every lose that password.

---

### Post by colin-schneider1996 on 2014-12-16
no. all the settings are not on. without usb stick i have nothing to select from the boot menu.

---

### Post by oldfred on 2014-12-16
I think then you need to set the UEFI password.

---

### Post by cj2008 on 2014-12-19
@colin-schneider -- did you manage to get this working?

I have also tried to install Ubuntu 14.04 on a Samsung Ativ 9 Lite laptop and am hitting problems. Seems like the Samsung BIOS is not picking up grub at all, so I get a "All boot options tried" error when I start up.

I installed via USB and when I remove the USB and reboot, then everything works fine for the very first boot. But every time after that it fails....

Here is the boot-repair log: [http://paste.ubuntu.com/9568273/](http://paste.ubuntu.com/9568273/)

---

### Post by oldfred on 2014-12-19
Did you try the rename of shim's entry in UEFI to read Windows using efibootmgr as in post #2?
Preferred if it works as then grub updates do not have to be copied again.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Or perhaps Samsung&#8217;s do not just read the "Windows" description like it seems others do and you have to have the /EFI/Microsoft/Boot folder with bootmgfw.efi which we make be shim or grub and boot Windows entry but really grub or shim.
Or we create /EFI/Boot folder and create shim or grub as bootx64.efi and boot hard drive entry.
Either case will then require you to copy files again when grub has major updates or you may get boot errors where grub versions are different.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Your model and user created /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919&p=13106595#post13106595](http://ubuntuforums.org/showthread.php?t=2230919&p=13106595#post13106595)

This was an HP, but only Ubuntu and creating Microsoft folders.

 Ubuntu only on HP, recreate Windows folder and grub as Windows boot file
[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)
    From live installer mount the efi partition on hard drive:
    mount /dev/sda1 /mnt
    cd /mnt/EFI

       use ls to see if created correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by cj2008 on 2014-12-19
Thanks oldfred.

Managed to get this working. Here are my steps:

1) Boot into live installer
2) sudo mount /dev/sda1 /mnt
3) cd /mnt/EFI
4) mkdir boot
5) sudo cp ubuntu/grubx64.efi boot/bootx64.efi
6) Remove UBS key and reboot

---

### Post by oldfred on 2014-12-19
Glad that worked.

So you can boot the hard drive entry and do not have to create a "Windows" efi boot entry, although that is another option.

---

### Post by cj2008 on 2014-12-20
Actually I tried creating EFI/Microsoft/Boot/ and copying grub in there first but it didn't work for me -- the Samsung BIOS never recognised it as a boot option.
On my machine it only picked it up when I did the same action in EFI/boot.

Thanks again for your help.

---

### Post by Maheriano on 2015-01-12
> **cj2008 said:**
> Thanks oldfred.

Managed to get this working. Here are my steps:

1) Boot into live installer
2) sudo mount /dev/sda1 /mnt
3) cd /mnt/EFI
4) mkdir boot
5) sudo cp ubuntu/grubx64.efi boot/bootx64.efi
6) Remove UBS key and reboot

Thank you very much! I spent 2 days trying to get Ubuntu installed on my Samsung Book 9 and doing this is what finally worked!

---

