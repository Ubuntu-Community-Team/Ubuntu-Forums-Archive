---
title: "installed ubuntu to usb, didn't change boot loader installation, cant boot windows"
date: 2015-07-23
forum: Installation &amp; Upgrades
---

### Post by thegadgetwhiz on 2015-07-23
I was trying to create a persistent usb stick, with everything  contained on the usb (including grub or whatever). I used the live cd to  install and was pretty sure I changed the boot loader installation to  the usb stick, but apparently I didn't. Atleast thats the only way I  could see this happening. I restart my computer and it gives me a list  of options to boot from, windows, ubuntu, etc.


  Thats not what I wanted, I wanted to only boot ubuntu when I selected  the usb stick. I boot back up the live cd and redo the usb installation  being extra careful. Now I can boot the usb like I want to. **I basically reformatted the usb stick and reinstalled ubuntu the right way.** The problem is I can no longer boot windows. It doesn't even give me a selection like it did before (windows, ubuntu, etc) instead it just has a grub command line thing.


  I had two hard drives attached at the time, an ssd with my windows 8  installation and an hdd with some files. I unplugged the hdd and grub  still appears so I guess the ssd is what I need to worry about.


  I tried inserting my windows repair disk and running all of the  bootrec commands and nothing worked. Then I tried installing the  boot-repair tool on the linux live cd and ran the recommended settings  and that didn't do anything. I also installed the os-uninstaller and it  didn't show me a list of os's, it automatically wanted to wipe the  windows bootloader or something.


  Anyways, here is the file the boot-repair tool generated
  [http://paste.ubuntu.com/11927598/](http://paste.ubuntu.com/11927598/)


  When my computer starts it says GNU GRUB version 2.02, minimal bash-like etc
  then
  grub>_


  Of course, if I try to boot from the ssd, it says reboot and select  proper boot device. My motherboard is a gigabyte 990fxa-ud3. I'm not  really sure if I'm using uefi or not.

---

### Post by oldfred on 2015-07-24
Your Windows install is UEFI on sda which is a gpt partitioned drive. Windows only boots in UEFI mode from gpt partitioned drives. And only boots in BIOS mode from MBR(msdos) drives.

Since UEFI, you should be able to just go into UEFI and choose to boot the Windows UEFI entry from boot tab. Many systems also have a one time boot key like f10 or f12 to choose the boot entries without going into UEFI.

But some fix you ran installed a Windows BIOS boot loader on sda, which will never work. Just do not try booting in BIOS mode from sda. The protective MBR on a gpt drive is not used, so as long as you do not try to boot having it there is not an issue.

It looks like at some point you did a full install of Ubuntu to some device, but that is not now connected when you ran the Summary Repair.

What brand & model system? What video card/chip?

It looks like you booted Boot-Repair in BIOS mode. But then it tries to do BIOS fixes, which you do not want. Once you have UEFI, you really should have all drives as gpt partitioned and always boot in UEFI mode.

Your sdb is MBR partitioned. At some point in future you may want to convert to gpt, but not a requirement.

Plug external drive back in, boot Boot-Repair in UEFI mode and post new link to a new summary report.

Grub does have an issue with installing to second drives when in UEFI mode. It only installs to sda. It overwrote my main working install's UEFI entry in sda, when I installed to sdb. It even said it was installing to sdb, but installed to sda.

So I backup efi partition on sda. And manually partition any other drive with gpt and have to have the efi partition best if first partition on drive. Then you can copy ubuntu folder from sda's efi partition to sdb's efi partition. But if an external device you also have to copy files to /efi/Boot and rename grub or shim to bootx64.efi as UEFI only boots bootx64.efi from external devices.

---

### Post by thegadgetwhiz on 2015-07-24
> **oldfred said:**
> Your Windows install is UEFI on sda which is a gpt partitioned drive. Windows only boots in UEFI mode from gpt partitioned drives. And only boots in BIOS mode from MBR(msdos) drives.

Since UEFI, you should be able to just go into UEFI and choose to boot the Windows UEFI entry from boot tab. Many systems also have a one time boot key like f10 or f12 to choose the boot entries without going into UEFI.

But some fix you ran installed a Windows BIOS boot loader on sda, which will never work. Just do not try booting in BIOS mode from sda. The protective MBR on a gpt drive is not used, so as long as you do not try to boot having it there is not an issue.

It looks like at some point you did a full install of Ubuntu to some device, but that is not now connected when you ran the Summary Repair.

What brand & model system? What video card/chip?

It looks like you booted Boot-Repair in BIOS mode. But then it tries to do BIOS fixes, which you do not want. Once you have UEFI, you really should have all drives as gpt partitioned and always boot in UEFI mode.

Your sdb is MBR partitioned. At some point in future you may want to convert to gpt, but not a requirement.

Plug external drive back in, boot Boot-Repair in UEFI mode and post new link to a new summary report.

Grub does have an issue with installing to second drives when in UEFI mode. It only installs to sda. It overwrote my main working install's UEFI entry in sda, when I installed to sdb. It even said it was installing to sdb, but installed to sda.

So I backup efi partition on sda. And manually partition any other drive with gpt and have to have the efi partition best if first partition on drive. Then you can copy ubuntu folder from sda's efi partition to sdb's efi partition. But if an external device you also have to copy files to /efi/Boot and rename grub or shim to bootx64.efi as UEFI only boots bootx64.efi from external devices.

Since the first post, I messed around with a couple things and probably did more harm than good. I changed a couple options in the boot-repair, and tried using efibootmgr.

I did make a little bit of progress though, I do have an option to uefi boot the ssd. Before I never had this option. But it doesnt boot windows. It either boots windows repair, or just sits there and loads.

Like I said I have a gigabyte mobo 990fxa-ud3. The video card is some crappy radeon HD 4xxx something.

Also, I noticed I could boot the livecd in legacy or uefi, So I tried using boot repair in both. I wasn't sure if it made a difference.

Here is a log of efibootmgr -v:

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0008
Timeout: 3 seconds
BootOrder: 0000,0005,0008,0004,0007
Boot0000* ubuntu    HD(1,800,100000,b85080ef-506e-4463-9245-9722d31822b9)File(\EFI\ubuntu\shimx64.efi)
Boot0004* CD/DVD Drive     BIOS(3,0,00)AMGOAMNO........o.A.S.U.S. . . . .D.R.W.-.2.4.B.1.S.T. . . .i....................A...........................>..Gd-.;.A..MQ..L.A.D.0.D.L.C.3.0.8.5.3.4. . . . . . . . ......AMBO
Boot0005* UEFI: ADATA SP900    HD(2,96800,32000,046ced0f-fa32-4714-82f5-e75cacf29dcd)File(\EFI\BOOT\BOOTX64.EFI)AMBO
Boot0007* Hard Drive     BIOS(2,0,00)AMGOAMNO........o.A.D.A.T.A. .S.P.9.0.0....................A...........................>..Gd-.;.A..MQ..L.D.7.3.3.0.2.0.0.7.9.3.6. . . . . . . . ......AMBOAMNO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.0.8.M.2.N.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.3.C.1.F.1.7.4.5.0.9......AMBO
Boot0008* UEFI: ASUS    DRW-24B1ST   i    ACPI(a0341d0,0)PCI(11,0)03120a000200ffff0000CD-ROM(1,1429,1240)AMBO
ubuntu@ubuntu:~$
```

And here is the paste bin of boot-repair in uefi mode with all hard drives plugged in:

[http://paste.ubuntu.com/11931734/](http://paste.ubuntu.com/11931734/)

Here's a picture of the options in my boot menu, plus some pictures of windows trying to boot

[https://goo.gl/photos/KtWpyBNXF8G42X25A](https://goo.gl/photos/KtWpyBNXF8G42X25A)

---

### Post by oldfred on 2015-07-24
In BIOS boot flag is on WIndows partition or Windows boot partition with boot files.
But with UEFI the boot flag is used to tell UEFI that the ESP - efi system partition is where to find efi boot files. You can only have one ESP per device. 
Remove boot flag from sda4, then UEFI boot may work.

It looks like you left Windows with fast boot or its always on hibernation on. It must be off.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Many with Gigabyte have issues with IOMMU.
       
  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

Make sure you have the latest UEFI update from Gigabyte.

Usually best to have secure boot off in UEFI, but UEFI on or CSM/BIOS/Legacy off.

You may need to add Windows entry back into your UEFI: your ESP is sda2, so you need the added entry:

 New Windows entry - assumes default sda1,   add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

More details on efibootmgr settings & parameters:

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Still not showing 3rd drive with Ubuntu install?

---

### Post by thegadgetwhiz on 2015-07-24
Can you give me instructions on how to remove the boot flag on sda4?

I can't shut off fastboot if my computer doesnt start.

I have IOMMU turned on in my bios.

So I would do:
[COLOR=#000000]sudo efibootmgr -c -p 2 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

Like I said I originally insalled linux to the usb stick (the wrong way), but then wiped the usb stick and reinstalled it the right way onto the usb, so the usb is no longer part of the problem.
I want to complety remove anything linux from my system (all parts of linux are on the usb stick).

Still new to linux so sorry for my ignorance.[/COLOR]

---

### Post by thegadgetwhiz on 2015-07-26
> **oldfred said:**
> In BIOS boot flag is on WIndows partition or Windows boot partition with boot files.
But with UEFI the boot flag is used to tell UEFI that the ESP - efi system partition is where to find efi boot files. You can only have one ESP per device. 
Remove boot flag from sda4, then UEFI boot may work.

It looks like you left Windows with fast boot or its always on hibernation on. It must be off.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Many with Gigabyte have issues with IOMMU.
       
  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

Make sure you have the latest UEFI update from Gigabyte.

Usually best to have secure boot off in UEFI, but UEFI on or CSM/BIOS/Legacy off.

You may need to add Windows entry back into your UEFI: your ESP is sda2, so you need the added entry:

 New Windows entry - assumes default sda1,   add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

More details on efibootmgr settings & parameters:

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Still not showing 3rd drive with Ubuntu install?

Still looking for help. Haven't done anything since because I don't want to mess it up anymore than it is.

---

### Post by oldfred on 2015-07-26
You can use gparted, right click on partition and change flag settings. Click to check icon to actually make change.
You can use Disks, but do not know details
Command line.
sudo parted /dev/sda set 4 bios_grub off

With gpt(GUID) it really is a very long GUID code assigned to partition.
Gparted & parted use boot flag to assign correct GUID.

You can use gdisk can change code from ef00 to 8300. That is the code it uses.
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


sudo apt-get install gdisk
sudo gdisk -l /dev/sda

That looks like the correct efibootmgr entry.
Afterwards run this to see if it shows and the test it to see if it works.
sudo efibootmgr -v

---

### Post by ubfan1 on 2015-07-26
Your efibootmgr command is right, adding the -p 2 for the second partition location.  That should create a Windows entry in the EFIbootmgr -v list.  You should be able to select that entry with the efi boot choice at power-up.  If it works, you can change the bootorder with efibootmgr with the -o switch (In a terminal run   man efibootmgr   for details).  Use gdisk to remove the boot attribute (x to get to expert mode, then a for attributes, then look at the number, subtract the number for boot, and reset it.

---

