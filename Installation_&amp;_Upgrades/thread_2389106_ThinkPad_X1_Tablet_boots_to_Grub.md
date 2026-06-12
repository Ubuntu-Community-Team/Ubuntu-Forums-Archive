---
title: "ThinkPad X1 Tablet boots to Grub"
date: 2018-04-11
forum: Installation &amp; Upgrades
---

### Post by stockcar on 2018-04-11
Hello,

I have a newer ThinkPad X1 Tablet with Windows 10.  I tried installing Ubuntu to a Micro SD card and the computer now boots to the Grub> prompt.

I can type exit and then boot into Windows.  Is there a way to fix this to boot to either Widows or the SD card via a menu?

Note:  When I restart, hit F12 for the boot device list, and select the SD card, it will NOT boot to Ubuntu, the Grub> prompt just comes up again.

I have installed the grub-repair and created the following analysis.

   [http://paste.ubuntu.com/p/xgJj7tT89Y/](http://paste.ubuntu.com/p/xgJj7tT89Y/)

Thanks!

---

### Post by oldfred on 2018-04-11
You do not have SD card in system?

You have grub trying to boot from a partition whose UUID is not shown in list of UUIDs.
And files in SD card seem to be an installer, not an actual install.

Line 133
 search.fs_uuid 2d4c5488-4068-4725-8da4-54fd63019de8 root  

And then you have grub/Ubuntu as default boot in UEFI.
Line 314

   BootOrder: 0001,0009,0000,0006,0005,0007,0008,000A
Boot0000* Windows Boot Manager    HD(1,GPT,b036c88e-0df1-4218-8ff3-bc4cece30b9d,0x800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)
Boot0001* ubuntu    HD(1,GPT,b036c88e-0df1-4218-8ff3-bc4cece30b9d,0x800,0x82000)/File(EFIubuntushimx64.efi) 

You should be able to go directly into UEFI can change boot order to have Windows first.
Or use efibootmgr to change boot order.
See 
man efibootmgr

       Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 0000,0001

---

### Post by stockcar on 2018-04-13
Thank you for the reply and information.

It is a built in MicroSD card reader on the back of the tablet.

I was able to use EasyUEFI in Windows for fix one of the problems, moved Windows to the top of the boot order, and now upon restart in goes right to Windows instead of booting to grub>

So, I still have a problem where when I select Ubuntu from the boot menu, pointing to my MicroSD card, it still does not boot Ubuntu, rather it just starts with the grub> prompt.

Here is what I see in the boot menu from EasyUEFI:
Description:ubuntu
GPT partition GUID:{B036C88E-0DF1-4218-8FF3-BC4CECE30B9D}
Partition number:1
Partition starting sector:2048
Partition ending sector:534527
File path:\EFI\ubuntu\shimx64.efi

At this point, not sure if the tablet really supports boot to the SD.

---

### Post by oldfred on 2018-04-13
If you plug MMC card into USB adapter, does it then work?
Every system will boot from USB, although some require turning on, or allowing USB boot in UEFI settings.

---

### Post by stockcar on 2018-04-27
I do not have a MMC card, however, I think I have given up and trying to boot from the SD card.  I have installed Ubuntu on a USB and the boot works fine when the USB is in the tablet.

When I restart the PC, I am back to getting the grub> and have to type exit to get windows to run.  I can change the boot order and Windows boots fine.  Just not sure if I should get the grub> prompt when booting without the USB in the PC or if there is a grub boot issue I might want to resolve?

---

### Post by oldfred on 2018-04-27
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by stockcar on 2018-04-29
Boot info report [http://paste.ubuntu.com/p/yyTFQCVV6g/](http://paste.ubuntu.com/p/yyTFQCVV6g/)

---

### Post by oldfred on 2018-04-29
Your UEFI shows the Ubuntu entry is in sda1 and that has a grub.cfg trying to boot from sdc1.
UEFI uses GUID , grub uses UUID.

 Line 1216 UEFI boot entry - GUID:
Boot0000* ubuntu	HD(1,GPT,[COLOR=#ff0000]b036c88e-0df1-4218-8ff3-bc4cece30b9d[/COLOR],0x800,0x82000)/File(EFIubuntushimx64.efi)
line 685  UEFI uses GUID/PARTUUID, grub uses UUID
/dev/sda1: LABEL="SYSTEM" UUID="58C5-D040" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="[COLOR=#ff0000]b036c88e-0df1-4218-8ff3-bc4cece30b9d[/COLOR]"
dev/sdc1: UUID="[COLOR=#b22222]973f34fb-9c6b-4828-837b-0be6f48571dd[/COLOR]" TYPE="ext4" PARTUUID="0001e867-01"
Line 185 has grub in ESP on sda1, trying to fine full grub.cfg in sdc1
search.fs_uuid [COLOR=#b22222]973f34fb-9c6b-4828-837b-0be6f48571dd[/COLOR] root hd2,msdos1  

That sequence looks correct.
Grub install looks like it worked, error seems to be related to sdb, which is your live installer.

Do not know if sdc being MBR, not gpt makes a difference. It should work although with UEFI gpt is standard, but live installer can be MBR and works to boot installer.

Do you have UEFI set to allow full USB access. Some require special settings to use USB for booting.

If you want to directly boot from sdc, it has to be totally reconfigured.

---

