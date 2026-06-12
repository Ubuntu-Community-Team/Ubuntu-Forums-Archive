---
title: "dual boot windows 10 after ubuntu 16.04"
date: 2017-07-31
forum: Installation &amp; Upgrades
---

### Post by aliole4731 on 2017-07-31
I followed the steps given here :[https://www.linuxdeveloper.space/install-windows-after-linux/](https://www.linuxdeveloper.space/install-windows-after-linux/)
on a friends laptop and his dual boot ( ubuntu and windows) runs perfectly.Now when i tried the same steps on my laptop there was a problem.
I created a separate partition for windows (ntfs) and when I tried installing windows in that partition i get a warning saying:**CAN'T INSTALL WINDOWS IN "THIS PARTITION"-PARTITION OF GPT STYLE.**
Should I change my partition to mbr type?if yes,any suggestions on how it can be done?

---

### Post by oldfred on 2017-07-31
Normally if drive is gpt, then it is a newer UEFI system. And Ubuntu is probably installed in UEFI boot mode.
You can just boot Windows installer in UEFI boot mode. You should have two boot options from UEFI boot menu on booting USB flash drive.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

If you really want to go back to the now 35 year old BIOS/MBR configuration, you may be able to convert drive to MBR, and reinstall grub.
But Windows then must be installed to a primary NTFS partition with boot flag. So it may depend on how many partitions you have used on whether somewhat difficult or very difficult to convert new system to old configuration.
Post this:
       
 sudo parted /dev/sda unit s print

---

### Post by aliole4731 on 2017-07-31
yes I have two boot options but the UEFI one does not work.I would hate to go back to the older configuration but i don't see an alternative since UEFI does not boot.Is there a way to create a UEFI only bootable device?
I created bootable usb from a win 10 iso file using multisystem and woeusb apps.Each time the uefi version did not boot and the bios/legacy version would show the "**CAN'T INSTALL WINDOWS IN "THIS PARTITION"-PARTITION OF GPT STYLE**" error.

---

### Post by oldfred on 2017-07-31
Both Ubuntu & Windows installers, install in the same mode as booted. So if booting installer in BIOS mode it will only install in BIOS boot mode.
And Windows only boots in UEFI mode from gpt.
And Windows only boots in BIOS mode from MBR(msdos).

Best to figure out why you cannot boot in UEFI mode. 
Older Windows 7 installers need files moved around.

I did not know Multi-system supported Windows installer.

       Make Windows bootable installer from Ubuntu
[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)
[https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011](https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011)
[http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu)

---

### Post by aliole4731 on 2017-08-01
I don't think there is a problem with my method of making Windows bootable installer.I have used Woeusb ,multisystem and i even used rufus (on a windows pc) to make a bootable device and each time the uefi version in the boot menu did not work.
i used the steps given here[ https://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu]("https://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu")
1.created a GPT partitioned usb.
2.created a  new primary partition and formatted it to fat32.
[ATTACH=CONFIG]276194[/ATTACH]
3.no missing bootx64.efi 
What am I doing wrong?Is something wrong with my laptop?

---

### Post by oldfred on 2017-08-01
What brand/model system?
Some older HP do not boot from gpt partitioned installers. Some only boot from specific USB ports.
Many must have UEFI set to UEFI boot on USB ports.

My Asus motherboard had UEFI and UEFI or BIOS as boot option settings for USB drives. But even the UEFI or BIOS setting only booted in BIOS mode. I had to change UEFI setting to UEFI only on USB to get it to boot in UEFI mode.

---

### Post by aliole4731 on 2017-08-01
I use HP 15-g207ax .
also I tried booting with uefi only and it would not boot.

---

### Post by oldfred on 2017-08-01
HP violates UEFI spec and uses description as part of boot.

You have to do a work around.
HPs still boot a fallback or hard drive entry at /EFI/Boot/bootx64.efi.
Boot-Repair will create that if you check in advanced options "use the standard file".

Most HP already have an hard drive entry in UEFI, but if not we can add one.
But you will not be able to boot ubuntu entry with an HP.

After updates post this to see entries.
sudo efibootmgr -v

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

Before Boot-Repair did the copy, users manually copied files.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

