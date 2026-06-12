---
title: "Load Grub from Windows 10 Bootloader"
date: 2015-08-05
forum: Installation &amp; Upgrades
---

### Post by Caveman6 on 2015-08-05
My setup is a two disk (both GPT partitioned) setup where disk 1 is windows 10 and disk 2 is ubuntu 15.04. Windows was installed first, then ubuntu, both in UEFI mode. The ubuntu drive is a removable hard drive, and I noticed that when it is not connected, grub would not fully load to show me a list of operating systems. I restored the windows 10 bootloader and added an entry pointing to /EFI/ubuntu/grubx64.efi. This file was located on the disk 1 EFI partition. However when I select this entry on startup, the windows bootloader tells me that windows failed to start because files are missing. I loaded ubuntu again and installed grub using boot-repair to the disk 2 EFI partition to see if that would work. I added an entry in the windows bootloader to grubx64.efi on disk 2 but ended up with the same failure. Is it possible to load Grub from the windows 10 bootloader or is it possible to load grub without requiring disk 2 to be connected?

---

### Post by lukeiamyourfather on 2015-08-05
There's a freeware application EasyBCD which will modify the Windows boot loader to add Linux installs or various other installs. It doesn't support Windows 10 right now but it might in the near future. I think it can be done manually but I've never tried (always used EasyBCD before).

---

### Post by yancek on 2015-08-05
> Is it possible to load Grub from the windows 10 bootloader

It never has been in the past and if the different options you tried fail, apparently still isn't.   Third party software such as EasyBCD worked with MBR systems.  I don't know if it works with UEFI?  

>  is it possible to load grub without requiring disk 2 to be connected? 		

You have the Ubuntu Grub efi files on the first disk but the rest of the Grub files are on the second drive.  I don't think that would work but someone more familiar with UEFI may have different information?

---

### Post by oldfred on 2015-08-06
I have put full installs of Ubuntu on sdb & a flash drive. In both cases I specifically told it to install grub to that drive  not default sda. And it even said it was going to install to sdb, but it overwrote my main working Ubuntu /EFI/ubuntu in sda.

Did you create an ESP - efi system partition on sdb, the external drive?
If so copy /EFI/ubuntu to the ESP on sdb.
And copy /EFI/ubuntu to the ESP into /EFI/Boot
Then rename /EFI/Boot/shimx64.efi to bootx64.efi.

UEFI only boots from external drives with the /EFI/Boot/bootx64.efi. But if that is your standard grub or shim (secure boot grub) then it has to find the grub.cfg in /EFI/ubuntu in the same ESP.

When external drive is not connected you will need to use one time boot key often f10 or f12 to boot Windows.
You may be able to set in UEFI, the external drive as first (which will boot grub) and Windows second. Then if external not plugged in it should boot Windows directly.

       sudo efibootmgr -v
Shows details on setting boot order.

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by NoWayWin8 on 2015-08-06
> added an entry pointing to /EFI/ubuntu/grubx64.efi
One problem is the OS doesn't know that file path is on a different disk than Windows.

Use DISKPART to assign a drive letter (any unused drive letter will do) to the EFI volume on SSD. Then use BCDEDIT to add the GRUB entry using the volume letter at the beginning of the EFI file path.

Overall it might not work well having two EFI partitions, particularly if you want GRUB to boot Windows. With Secure Boot it might not work at all.

---

### Post by oldfred on 2015-08-06
You can add the -d  & -p parameter and tell it which drive, partition.
 efibootmgr -c -d /dev/sdX -p Y -l \EFI\ubuntu\grubx64.efi -L "Ubuntu"
sdX is drive, Y is efi partition 

To see entries:

 sudo efibootmgr -v

Details on efibootmgr

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

