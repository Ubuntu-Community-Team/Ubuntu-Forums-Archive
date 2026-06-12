---
title: "Portable USB HDD installation"
date: 2018-09-20
forum: Installation &amp; Upgrades
---

### Post by bphillips79 on 2018-09-20
Hey folks.  Pretty much a noob here.  I'm trying to do a portable install 18.04 onto my USB HDD.  In the past, when installing (using a jumpdrive) I would just select "something else" when installing and choose the hdd as the bootloader location so as to not install anything on my laptop (thus the portable part).  So I just tried installing on a new usb drive and while the install worked fine the drive isn't showing up in the boot manager menu (where I select windows, usb, etc).  I've done some Googling and I haven't come across anything which has helped address my problem.  I have seen some comments regarding the UEFI so I switched to Legacy in BIOS but no joy.  If someone could either explain what I need to do (in simple terms - I'm not that bright) or point me to an accurate explanation, I would greatly appreciate it.

---

### Post by oldfred on 2018-09-20
Legacy will still work if you install in Legacy/BIOS/CSM boot mode and then have system set to boot in that mode.

If UEFI, bit more effort required.
You must partition in advance using gpt and include an ESP - efi system partition. UEFI only boots external drives from /EFI/Boot/Bootx64.efi. That same file name is used by both Windows & Ubuntu installers. 
And Ubuntu's grub only installs to the ESP on first drive, usually sda, or first NVMe drive.
I copy all of /EFI/ubuntu from internal drive twice, once to /EFI/ubuntu as shimx64.efi expects to see that, and then to /EFI/Boot and rename shimx64.efi to bootx64.efi.
You do have to turn on in UEFI allow usb boot, but you must have do that to boot install media.

See also link in my signature.
       Full install to external drive.
[URL="https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator"]https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator
      [/URL]
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 
    [URL="https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator"]
[/URL]

---

### Post by C.S.Cameron on 2018-09-21
In BIOS select the USB HDD as first HDD and boot it.
In Terminal run "sudo update-grub".
This should add your Windows to the grub menu.

---

### Post by joshua-powers22 on 2018-09-25
I'm looking to do something similar, just one question, if I remove the hard drive Ubuntu and the grub bootloader is on will the internal normal windows drive boot like normal?

---

### Post by oldfred on 2018-09-25
Again depends on if UEFI or BIOS.
With BIOS, the BIOS turns boot over to boot loader in MBR and it starts boot process. But BIOS is so small, grub need more files. Part is core.img right after MBR, but menu is in the Ubuntu install. So you get grub> or grub rescue.
If UEFI and it sees /EFI/ubuntu folder it will try to boot it. And you get the same type of errors.

Generally with external drives that may not always be plugged in, best to have entire boot loader on external drive.

---

### Post by joshua-powers22 on 2018-09-25
Well here's what I want to do, I would like to install Ubuntu in a dual boot with windows 10, but I don't want to touch the windows 10 bootloader, I just want to have grub on some other drive (the ubuntu install drive) or an entire separate usb key, so when the drive is plugged in I get a choice to boot the windows drive or the ubuntu drive, if I remove the key (or the ubuntu drive because I screwed it up) I want to be able to boot back into windows 10 like nothing ever happened, now the portable ubuntu usb drive seems like how I want to go but will it give me an option to boot windows/ubuntu (cause it's an external hard drive plugged in the back of the desktop, I don't want to have to keep plugging/unplugging it to switch between windows and ubuntu)

---

### Post by ubfan1 on 2018-09-25
Making a UEFI bootable USB drive without altering the first hard disk bootloader(s)

Under legacy (non-UEFI), there's no problem.  You specify your USB as the target for
the bootloader, and that's where it's put. Under UEFI however, regardless of 
what you specify for the bootloader location, it will go to the first EFI partition
it finds (on the hard disk, not the USB). Add yourself to the bugs 1173457 and 1396379
and maybe this will be fixed.

Workarounds
 1) Remove the first hard disk, set up your EFI, root, swap, etc. partitions on the USB, then install.
   Replace the (untouched) hard disk.
   Set the first boot device to be the USB, when present, grub should offer the choice of
   Windows on first hard disk, or Ubuntu on the USB.  When the USB is not present, Windows
   should boot normally.
OR

 2) Use a disk partitioning tool like gparted or gdisk to remove the boot/ESP flags on the hard disk's
EFI Partition.  Have a properly set-up EFI partition on the USB target (boot flag, ESP flag).
Install, the only ESP found should be on the USB.  Replace the ESP/boot flags on the hdd.
(I haven't tried this procedure, which was suggested in the bug report).

OR

3) Set-up the USB partitions, and back-up the hdd's ESP.  The only expected file to 
be overwritten is /EFI/Boot/bootx64.efi, but backing up all the files is good, in case the
filesystem is corrupted. Do the install.  The shim/grub bootloader will get added to the
hdd's /EFI/ubuntu directory.  The /EFI/Boot/bootx64.efi (originally the Windows bootloader) will
be overwritten by shim or grub (depending upon the secure boot setting).  Copy  the hdd's EFI partition
(everything under /EFI...) to the USB's EFI partition.  The USB is not bootable under UEFI.  Replace
the /EFI/Boot/bootx64.efi with the backup.  This bootloader is not/rarely used, it's a fallback
bootloader which may be invoked if the first bootloader fails, before the second one is used.
Delete the nvram entry for ubuntu from the hdd's /EFI/ubuntu/grubx64.efi (or shim) with efibootmgr.  Add an entry 
for the USB.

---

### Post by bphillips79 on 2018-09-26
Sooo....basically if legacy doesn't work (which it doesn't appear to be) then the only way is UEFI and for that to work I have to overwrite my current windows boot loader because GRUB will only install to the main drive?  This is way more complicated than it used to be.  With Ubuntu 16 and 17 it was super easy to install via the installer.

---

### Post by ubfan1 on 2018-09-26
Adding the /EFI/ubuntu directory in no way overwrites anything in /EFI/Microsoft/... whrere the Windows bootloaders are.  Only a fallback bootloader is overwritten, and it probably is never used, unless the disk becomes a removable media by putting it into an external USB/Esata box.  The boot order is changed to put grub first.  If  you don't want to boot grub, use the EFI boot menu and chose Windows, or put Windows before grub in the boot order with efibootmgr and use the EFI menu to boot grub -- your choice.

---

### Post by sudodus on 2018-09-27
If you can (and are willing to) disconnect your internal drive, you can install Ubuntu to the USB HDD according to the following link and links from it.

[How do I install Ubuntu to a USB key? (without using Startup Disk Creator) - Stepwise instructions](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

---

