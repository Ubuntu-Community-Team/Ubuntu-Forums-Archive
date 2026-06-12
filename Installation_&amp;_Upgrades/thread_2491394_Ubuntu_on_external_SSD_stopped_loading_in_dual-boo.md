---
title: "Ubuntu on external SSD stopped loading in dual-boot setup with Windows"
date: 2023-10-06
forum: Installation &amp; Upgrades
---

### Post by pp12pp on 2023-10-06
Hello, I have Ubuntu installed on external SSD and Windows on internal SSD. To boot into one of the system I was choosing which OS to run from GRUB screen. When SSD was unplugged, nothing would run at all. So it had to be connected to be able to choose Windows to run. 
This was until today. 

Today suddenly (I haven't done anything specific) GRUB screen stopped showing up and it goes straight to Windows. Can't boot into Ubuntu at all. I was trying to change boot order in BIOS, but no success. When I deactivate Windows boot option in BIOS, nothing boots, just enters BIOS over and over again. 

So I booted from another pendrive (here as sdd1) and got this boot-repair result [https://pastebin.com/raw/mNHHNvk8](https://pastebin.com/raw/mNHHNvk8) (I also paste part of it below)

Basically, I'd like to ask You if I can restore option do boot from Ubuntu, which is in this report as sdc1. 

Other than that, I'm curious about that:
- are the 'Boot files' from sdb2 pointing to systems that can boot, i.e. Windows on the same drive or Ubuntu on other drive?
- did this sdc1 drive lost Boot sector type somehow?
-** can I make this external SSD bootable and use on other computers? **That would be the coolest option


Here is the part of boot-repair info:
```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /bootmgr /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi



```
Thanks!

---

### Post by ubfan1 on 2023-10-06
See [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) Grub installs to wrong disk. Do add yourself to the "Does this affect me?" list on the bug.  In your case, grub is simply on another disk (no EFI partition on your Ubuntu disk). -- same problem, grub needs the disk with Ubuntu's root for the rest of its files. Even if you had added an EFI partition on sdc, the 22.04 installer would have ignored any "bootloader location", and put it on the first ESP found (sdb probably).
Another problem is that your host system probably will not boot without the external device (since needed grub files are on it).

Windows updates sometimes changes the bootorder, and puts itself first, or maybe just replaces the default bootloader ...EFI/Boot/bootx64.efi (which is a copy of grubx64.efi or shimx64.efi after a grub install) with a copy of its bootloader bootmgfw.efi. Then the device boot just boots Windows.

You can certainly fix things -- put an EFI partition on your Ubuntu disk (300MG, FAT, flags boot,esp), and put that device first in the bootorder. Then without that disk, the next boot should be the Windows boot.  To ensure that, you need to clean up the ESP on sdb (have its bootx64.efi be the windows bootmgfw.efi), and move the windows selection in the bootorder up to second place.

---

### Post by pp12pp on 2023-10-06
Do I unterstand correctly, the first part of solution that You suggest similar to what boot-repair is suggesting? And then second part (`Final advice`) is different?
```

Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sdc1,
using the following options:  sdb2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sdb2/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
```

> Another problem is that your host system probably will not boot without the external device (since needed grub files are on it).
It did not boot without external device but now it does.


Could currently this sdc boot from another computer?

---

### Post by oldfred on 2023-10-06
You have UEFI system and it looks like installs are now UEFI, you show both a Windows UEFI boot entry and multiple duplicate Ubuntu entries in ESP n sdb2.

If sdc is Ubuntu drive, you first need to add the ESP - efi system partition to that drive. Once grub files are reinstalled to that drive, then that drive can be booted in UEFI mode from any UEFI system, just like the live installer flash drive, by selecting the drive, not an "ubuntu" entry. If always booting on same drive, new UEFI entries with that GUID/partUUID will allow you to boot an "ubuntu" entry. Some UEFI change/modify/delete UEFI boot entry for any drive that is disconnected. 

Installer & full installs on external drive actually use /EFI/Boot/bootx64.efi or a drive entry. Many UEFI also have a drive entry for the internal drive, but bootx64.efi may be a copy of Windows .efi boot file or grub/shim's .efi boot file.

So first create new ESP on Ubuntu drive with gparted and then use Boot-Repair to do complete reinstall of grub to that drive. You may need to use advanced mode as default often is just an update to grub menu or reinstall. 
You also need to update fstab with new ESP's UUID, so major updates to grub are reinstalled to correct drive. Not sure if reinstall of grub will fix that, best to verify it has correct UUID.

To see UEFI entries.
sudo efibootmgr -v  #must be booted in UEFI mode
to see UUIDs & partUUID/GUIDs
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

to see fstab or mount once booted into install:
cat /etc/fstab
mount

---

### Post by pp12pp on 2023-10-14
Thank You for the responses. 

I've made ESP partition with gparted. Then I've tried to use boot-repair advanced mode, but unfortunately it wanted to mess something in Windows drive, so i stopped it in the process. It broke some entries that are visible in efibootmgr in a way that they throw some errors when I try force boot them from BIOS. But fortunately Windows is still booting. 

Then I've run grub-install pointing to that new partition. 

The SSD still isn't able to boot on this laptop1 and is not detected by BIOS as bootable device. (this laptop I can boot from Ubuntu Live USB stick)

I've tried booting this SSD on another laptop2 and it worked. 


I'd still like to boot this SSD from laptop1. 

What I understand is, that maybe some boot entries on the Windows boot partition make this SSD unavailable as boot device?

Current efibootmgr output (when booted from live USB)
```
$ efibootmgr -v
BootCurrent: 0009
Timeout: 0 seconds
BootOrder: 0000,0002,0007,0005,0006,0008,0009,0003
Boot0000* Windows Boot Manager    HD(2,GPT,d7d331fb-32bf-4abd-88ba-c92495af0f51,0x96800,0x31800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot0002* ubuext    HD(2,GPT,d7d331fb-32bf-4abd-88ba-c92495af0f51,0x96800,0x31800)/File(EFI\ubuntu\shimx64.efi)
Boot0003* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0005* ubugrub    HD(2,GPT,d7d331fb-32bf-4abd-88ba-c92495af0f51,0x96800,0x31800)/File(EFI\ubuntu\grubx64.efi)
Boot0006* ubummx    HD(2,GPT,d7d331fb-32bf-4abd-88ba-c92495af0f51,0x96800,0x31800)/File(EFI\ubuntu\mmx64.efi)
Boot0007* bootboot    HD(2,GPT,d7d331fb-32bf-4abd-88ba-c92495af0f51,0x96800,0x31800)/File(EFI\Boot\BOOTX64.EFI)
Boot0008* ubuntu    HD(2,GPT,d7d331fb-32bf-4abd-88ba-c92495af0f51,0x96800,0x31800)/File(\EFI\Ubuntu\grubx64.efi)
Boot0009* UEFI: KingstonDataTraveler 3.0PMAP    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,MBR,0xde81077,0x800,0x39bf800)..BO


```

Should I add new entry or edit existing one with this SSD UUID? 

Grub is installed on 8F92-88B2
```
$ lsblk -f /dev/sdd
NAME   FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
sdd                                                                           
&#9500;&#9472;sdd1 ext4   1.0         a4446e25-30c0-448a-ab7b-a261886e2fa4  375.4G    10% /media/ubuntu/a4446e25-30c0-448a-ab7b-a261886e2fa4
&#9492;&#9472;sdd2 vfat   FAT32       8F92-88B2      

```

.efi files in boot partition:
```
root@ubuntu:/media/ubuntu/a4446e25-30c0-448a-ab7b-a261886e2fa4# find boot/ -name "*.efi"
boot/grub/x86_64-efi/core.efi
boot/grub/x86_64-efi/grub.efi

```

fstab in this SSD (I've added last line by hand)
```
root@ubuntu:/media/ubuntu/a4446e25-30c0-448a-ab7b-a261886e2fa4# cat etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=a4446e25-30c0-448a-ab7b-a261886e2fa4 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
#UUID=8EA9-675C  /boot/efi       vfat    umask=0077      0       1
UUID=8F92-88B2  /boot/efi       vfat    umask=0077      0       1

```

---

### Post by oldfred on 2023-10-14
Your Boot-Repair report in first post has expired. It only lasts a short time.
Please run a new report. 

All your UEFI entries use the same GUID/partUUID which then must be the internal drive.
You can see the partUUID with the lsblk command in post #4. Compare UEFI entries using partUUID with lsblk entries.

If you updated fstab with external drive's ESP, and reinstalled grub, you should be able to boot external drive from a drive entry similar to how you boot live installer.
If you have UEFI secure boot on, only entries using shimx64.efi will work, grubx64.efi should work if UEFI secure boot is off. But I have Secure boot off on my system and it uses the shim file to boot.

---

### Post by pp12pp on 2023-10-14
My new boot-repair report [https://pastebin.com/NdRa96DS](https://pastebin.com/NdRa96DS)

Yes, indeed all UEFI entries points to internal drive. 

I am able to boot this SSD like live USB, but from second laptop, not from this first laptop. 

Secure boot in BIOS seems disabled. 

Ubuntu that I'd like to boot is now sdd1 and sdd2 is the new eps partition I've created. 
Laptop doesn't seem to recognize this SSD as bootable

lsblk output:
```

$ lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME FSTYPE   SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID                                 PARTUUID
sda         698.6G                                                                        
&#9492;&#9472;sda1
     ntfs   698.6G        Nowy  Basic data partition
                                                     3AC8ECA7C8EC629D                     8759b055-f4db-49a1-8241-71827454cc23
sdb         223.6G                                                                        
&#9500;&#9472;sdb1
&#9474;    ntfs     300M        Odzyskiwanie
&#9474;                               Basic data partition
&#9474;                                                    0210A8BE10A8BA55                     9e94bc32-e30b-4bbd-b9a6-da9e6f70c124
&#9500;&#9472;sdb2
&#9474;    vfat      99M              EFI system partition
&#9474;                                                    8EA9-675C                            d7d331fb-32bf-4abd-88ba-c92495af0f51
&#9500;&#9472;sdb3
&#9474;             128M              Microsoft reserved partition
&#9474;                                                                                         4197838e-4cce-40be-a474-42b73a7e2bec
&#9492;&#9472;sdb4
     ntfs   223.1G              Basic data partition
                                                     A062B27362B24DB2                     84f6363f-129d-423d-9a1e-4477e50f7024
sdc          28.9G                                                                        
&#9492;&#9472;sdc1
     vfat    28.9G   4.6G UBUNTU 22_0
                                          /cdrom     E6C2-0806                            0de81077-01
sdd         931.5G                                                                        
&#9500;&#9472;sdd1
&#9474;    ext4   452.4G  46.2G                 /media/ubu a4446e25-30c0-448a-ab7b-a261886e2fa4 2f50f57d-01
&#9492;&#9472;sdd2
     vfat     600M   6.1M                 /media/eps 8F92-88B2                            2f50f57d-02
 
```

---

### Post by oldfred on 2023-10-14
UEFI system with both installs as UEFI.
But you have BIOS boot loaders in sdb & sdc (which as live installs has two boot options). As long as you never try to boot in BIOS mode, having those there is ok. The one on sdb just will not work and you never want to boot live installer in BIOS mode.

You seem to have garbage in sdb2/efi/ubuntu/grub.cfg
in line 240, should be similar to line 298.
Looks like if you had an UEFI entry to boot install on sdd, it would work.

So two fixes, one for three line grub in sdb & one to create boot entry in UEFI for external drive.
I would use Boot-Repair using its optional full reinstall of grub to sdb.
The run it again and do full reinstall of grub to sdd.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You can use efibootmgr to remove duplicate "ubuntu" entries in UEFI. You can keep one for Ubuntu & one for internal drive, but if fstab has ESP of external drive a major grub update will update that, and may not update internal drive's grub.
sudo efibootmgr -b XXXX -B  # removed entries. See also 
man efibootmgr

If you have not reconfigured Ubuntu on sdd, now would be the better time to correct it.
It has the very old (from 1980's) MBR(msdos) partitioning. UEFI strongly suggests gpt and Windows required gpt for UEFI boot.
Ubuntu does not require gpt, but probably should.
Ubuntu may not want to convert drive to gpt as some still have old Windows installs in BIOS mode and conversion from MBR to gpt totally erases a drive. So to avoid erasing a BIOS mode Windows Ubuntu does not default to gpt unless drive has no partitions.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

