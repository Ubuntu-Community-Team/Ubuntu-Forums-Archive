---
title: "Install Ubuntu 14.04 on external HDD with Windows 8.1 UEFI"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by sander8 on 2015-06-06
Hey everyone,

First time posting question.
I recently bought a new laptop, Lenovo Essential B50-70 MCC39MB Azerty, and I had an external HDD lying around with ubuntu 14.04 on it. I thought it would be nice if I could use this HDD whenever I wanted. Just plug it in and choose ubuntu in GRUB. So I followed these instructions: [http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/](http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/). But now I have this problem that when the external HDD is not connected, I get an error from GRUB. When I type 'exit', I can boot into Windows but this is not really practical. I just want the GRUB to show up when the HDD is connected, and boot into Windows otherwise.

I already searched for a bit and didn't really find an answer to this specific problem. Any help is greatly appreciated.

Thank you!

---

### Post by oldfred on 2015-06-06
Did you install in UEFI boot mode or BIOS boot mode?
May be best to see details. You can run from live installer or you Install.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2015-06-06
Is Grub installed on the external drive. By default Grub is installed to sda. Go back to that tutorial and look at section 11 and compare the image there with the image in section 12.

> The most important thing you need to do here is ensure that the external  HDD is the device where the boot loader will be installed. You do that  by selecting **/dev/sdb** from the menu.

Please confirm.

Regards.

---

### Post by sander8 on 2015-06-07
I did that, so Grub should be installed to sdb.

---

### Post by sander8 on 2015-06-08
[http://paste.ubuntu.com/11646802/](http://paste.ubuntu.com/11646802/) This is the link to the boot-repair. I already once executed the recommended repairs hoping to fix the problem. But they didn't :(

---

### Post by oldfred on 2015-06-08
Your external drive is MBR which is really only for BIOS booting not UEFI.
But Boot-Repair and perhaps Ubuntu installer will install to a MBR drive, but put UEFI boot loaders in a different drive that is gpt partitioned and has an efi partition. 
If you want UEFI boot you need to change sdb to gpt partitioning. Usually best to fully backup and just repartion which will erase it. But there are tools to convert to gpt, but backup still required.

Or you can just reinstall in BIOS boot mode with grub in MBR on sdb. You will have to switch system from UEFI to BIOS and vice-versa to boot system installed in that mode.
Converting to or from GPT
 [http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by sander8 on 2015-06-10
Yeah, I read that somewhere that might have been the problem too.

It will be the next thing I try.

Thank you for your help and I will post when I have tried partitioning to gpt.

---

### Post by sander8 on 2015-07-13
Ok,

It has been awhile since I responded but I have been busy. Now I have partitioned the disk in gpt. I set the bootloader on a seperate EFI partition on the external disk. Now I'm stuck again.
When booting and external hdd is not connected, I get a grub error. Typing 'exit' I can boot to Windows but this is a lot of overhead.
There are a lot of differrent approaches to solve this. At least according to the internet... But I'm lost.
Any of you have a suggestion?

The setup I want is that when I plug in the disk, it will show the grub and I will be able to choose whether to boot in ubuntu or windows.
But I don't want to boot to ubuntu via USB. I want ubuntu specifically. As in I don't want USB boot to be before windows boot loader, only when it is the ubuntu disk... if that makes any sense.
That way it wouldn't be possible to boot a random USB device.

Thanks in advance for your help.

---

### Post by oldfred on 2015-07-13
I have not been able to get grub to correctly install to a second drive's efi partition. It always installs to sda's efi partition.
I have both a sdb drive and full installs on a flash drive in UEFI mode.

If you created an efi partition on the external drive, you need to copy the /EFI/ubuntu folder to the external drive. But USB external drives boot in UEFI mode from /EFI/Boot/bootx64.efi. So then from /EFI/ubuntu copy grub or shim into /EFI/Boot and rename to bootx64.efi. That should let you choose to boot external. It actually uses the /EFI/ubuntu/grub.cfg which has the UUID of the install in it to find the grub.cfg in the install.

You may need to remove /EFI/ubuntu from internal drive's efi partition. And houseclean UEFI entries. But make sure you can manually boot external drive first.

---

### Post by sander8 on 2015-07-14
Thanks for the quick reply.

In my case, the only files in efi in the C:\ drive are in the boot folder. There's no ubuntu folder. I looked at /boot in ubuntu on the external drive and there are files similar to those in \efi on the C:\ drive. Do I copy those? And which ones?

Sorry I'm such a tough customer, I'm always there I think though.

---

### Post by oldfred on 2015-07-14
Your install may not have created an ESP - Efi System Partition on external drive.
I always have had to partition in advance with gparted and select gpt before anything else. And add the efi partition first.

Post this from terminal:
sudo parted -l

---

### Post by sander8 on 2015-07-15
This is the output of sudo parted -l
```
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs         Basic data partition          hidden, diag
 2      1050MB  1322MB  273MB   fat32        EFI system partition          boot, hidden
 3      1322MB  2371MB  1049MB  fat32        Basic data partition          hidden
 4      2371MB  2505MB  134MB                Microsoft reserved partition  msftres
 5      2505MB  957GB   954GB   ntfs         Basic data partition          msftdata
 6      957GB   984GB   26,8GB  ntfs         Basic data partition          msftdata
 7      984GB   1000GB  16,4GB  ntfs         Basic data partition          hidden, diag


Model: WDC WD64 00BPVT-80HXZT1 (scsi)
Disk /dev/sdb: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  326MB  325MB   fat32           EFI System Partition  msftdata
 2      326MB   262GB  262GB   ntfs                                  msftdata
 3      262GB   525GB  262GB   ext4
 4      525GB   537GB  12,0GB  linux-swap(v1)
```

As I said, I created an EFI partition on the external disk and selected to use this as an EFISP. On installation I set this external EFI partition as bootloader and the EFI partition on the internal disk as "don't use this partition".
So do I copy the files of the external /boot directory? I think the needed files are in /boot/efi. This is the output of ls -R in /boot/efi:
```
.:
BOOT  EFI

./BOOT:
boot.sdi

./EFI:
Boot  Microsoft  ubuntu

./EFI/Boot:
bkpbootx64.efi  bootx64.efi

./EFI/Microsoft:
Boot

./EFI/Microsoft/Boot:
BCD           BOOTSTAT.DAT  en-US  hu-HU        nb-NO      ro-RO       tr-TR
BCD.LOG       boot.stl      es-ES  it-IT        nl-NL      ru-RU       uk-UA
BCD.LOG1      cs-CZ         et-EE  ja-JP        pl-PL      sk-SK       zh-CN
BCD.LOG2      da-DK         fi-FI  ko-KR        pt-BR      sl-SI       zh-HK
bg-BG         de-DE         Fonts  lt-LT        pt-PT      sr-Latn-CS  zh-TW
bootmgfw.efi  el-GR         fr-FR  lv-LV        qps-ploc   sr-Latn-RS
bootmgr.efi   en-GB         hr-HR  memtest.efi  Resources  sv-SE

./EFI/Microsoft/Boot/bg-BG:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/cs-CZ:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/da-DK:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/de-DE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/el-GR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/en-GB:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/en-US:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/es-ES:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/et-EE:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/fi-FI:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/Fonts:
chs_boot.ttf  malgun_boot.ttf   msjh_boot.ttf   segmono_boot.ttf
cht_boot.ttf  malgunn_boot.ttf  msjhn_boot.ttf  segoen_slboot.ttf
jpn_boot.ttf  meiryo_boot.ttf   msyh_boot.ttf   segoe_slboot.ttf
kor_boot.ttf  meiryon_boot.ttf  msyhn_boot.ttf  wgl4_boot.ttf

./EFI/Microsoft/Boot/fr-FR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/hr-HR:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/hu-HU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/it-IT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/ja-JP:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/ko-KR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/lt-LT:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/lv-LV:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/nb-NO:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/nl-NL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/pl-PL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/pt-BR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/pt-PT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/qps-ploc:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/Resources:
bootres.dll  en-US

./EFI/Microsoft/Boot/Resources/en-US:
bootres.dll.mui

./EFI/Microsoft/Boot/ro-RO:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/ru-RU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/sk-SK:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/sl-SI:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/sr-Latn-CS:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/sr-Latn-RS:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/sv-SE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/tr-TR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/uk-UA:
bootmgfw.efi.mui  bootmgr.efi.mui

./EFI/Microsoft/Boot/zh-CN:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/zh-HK:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/Microsoft/Boot/zh-TW:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

./EFI/ubuntu:
grub.cfg  grubx64.efi  MokManager.efi  shimx64.efi

```

Thanks for helping!

---

### Post by oldfred on 2015-07-15
Every time I have installed to sdb or external drive, it has added or overwritten my /EFI/ubuntu folder in sda.
I copied my /EFI/ubuntu folder to my sdb's efi partition.
If yours did not install, try using Boot-Repair to reinstall grub. The version of grub for UEFI boot on live install is somewhat different in its configuration, so best not to try to copy it.

If external drive UEFI expects to boot from the /EFI/Boot/bootx64.efi. So then copy /efi/ubuntu folder to /EFI/Boot and rename either grubx64.efi or shimx64.efi to bootx64.efi.
Note that even if you have grub.cfg in /EFI/Boot, it will use the grub.cfg in /EFI/ubuntu. And that grub.cfg is just a configfile to load the real grub.cfg in your install.

---

### Post by sander8 on 2015-07-26
Hey,

I'm still struggling to make it work. The following is the output of ```
sudo efibootmgr
```

```
BootOrder: 0002,0005,0006,2003,0003,2001,2002
Boot0000* EFI Network 0 for IPv4 (F0-76-1C-24-DE-8A)     ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f0761c24de8a,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0001* EFI Network 0 for IPv6 (F0-76-1C-24-DE-8A)     ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f0761c24de8a,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* Windows Boot Manager    HD(2,1f4800,82000,1d15acfe-a3ac-4919-9860-41b0b9d18553)File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0003* Lenovo Recovery System    HD(3,276800,1f4000,d79bc656-c18c-48cd-87b6-0883e40a05a1)File(\EFI\Microsoft\Boot\LrsBootMgr.efi)RC
Boot0005* ubuntu    HD(2,1f4800,82000,1d15acfe-a3ac-4919-9860-41b0b9d18553)File(\EFI\ubuntu\shimx64.efi)
Boot0006* ubuntu    HD(3,276800,1f4000,d79bc656-c18c-48cd-87b6-0883e40a05a1)File(\EFI\ubuntu\shimx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
```

What do I need to put in the ESP of my external drive? And is the bootorder correct?

I want it in such a way that the grub doesn't show up every time, only when external drive is attached. What i got from your explanation is that is should put /EFI/ubuntu/shimx64.efi in my external drive's ESP or is that wrong?
Thanks!

---

### Post by oldfred on 2015-07-26
I believe this is what you want as first boot device and then Windows as second.
Boot2001* EFI USB Device    RC

The efi USB boot device will boot from the /EFI/Boot/bootx64.efi file on external drive.

Have you copied /EFI/ubuntu folder from sda to sdb? And then to sdb's /EFI/Boot folder?

If so see if you can boot from the EFI USB boot device.  Either from UEFI or one time boot key.

---

### Post by ubfan1 on 2015-07-26
You can leave the "boot" flag on both ESPs without any problem.  On the SSD the ESP's /EFI/Boot directory should contain bootx64.efi (which is a copy of shimx64.efi, the original one was a copy of Microsoft's bootloader), and also grubx64.efi (since shim only runs a local copy of grubx64.efi).  It's good to have the /EFI/ubuntu directory fully populated with shimx64.efi and grubx64.efi as a backup, and with grub.cfg which is where grubx64.efi looks for it, regardless of where grub is run.  
  Some possible issues:  The bootorder may get reset to hard disk first if you boot without the SSD (I have an Asus that does this).  That Asus also cannot boot USB when secure boot is enabled (but I don't have the EFI USB choice).

---

### Post by sander8 on 2015-07-26
I don't like the idea of putting USB device as first in the boot sequence. Is there any way to do this without putting the USB device as first one in the boot sequence?

---

### Post by oldfred on 2015-07-26
Use your one time boot key to boot USB whenever you have it plugged in. 
Most systems use f10 or f12 to give the UEFI boot menu directly.

---

### Post by sander8 on 2015-07-29
Am I correct to understand that one time boot is only performed from boot and not reboots?
Is there a way to put the ubuntu entry as the first one in the bootsequence and when it fails, than it must boot windows. Or is this not possible with UEFI?

---

### Post by oldfred on 2015-07-29
You should be able to change boot order in UEFI. Most have first, second type entries somewhere. 

You can also change with efibootmgr.
       [URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]
[/URL]# from liveDVD or flash booted in UEFI mode or working install and use efibootmgr
sudo efibootmgr -v
# from above list use numbers in order
efibootmgr -o 3,4

Also see example 3
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
Change boot order with efibootmgr, some require all 4 char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)[URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]
[/URL]


 
[URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]
[/URL]

---

