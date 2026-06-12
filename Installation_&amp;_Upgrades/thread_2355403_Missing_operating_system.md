---
title: "Missing operating system"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by adellis on 2017-03-12
I have a Intel NUC box that I use to run Ubuntu 16.04 LTS. It works fine but I had to update to a 4.8 kernel to make a TV USB stick work. I've recently moved to the 4.10 kernel and everything is fine but when grub updates it causes an unknown partition error to occur. I fixed it the first time by using boot-repair but this time it's hasn't fixed it and I've made it worse (probably by trying to reinstall the MBR) and now get a "Missing operating system" error. I tried boot-repair a few times with no success and am reluctant to try advanced options without knowing what I'm doing.

Boot-Repair generated the following details [http://paste.ubuntu.com/24165193/](http://paste.ubuntu.com/24165193/), but I can't see anything obvious.

Any help gratefully received.

Regards

Adrian

---

### Post by oldfred on 2017-03-12
Did drive order get switched?

Grub only installs to the ESP - efi system partition on sda. 
But fstab says ESP was on sdb1?

You do not show any ESP on sda, just two Linux partitions, and it does not specifically say gpt?
And sdb shows two ESPs? You can only have one per drive.
Remove boot flag from sdb2.

You also show syslinux BIOS boot in MBR. But with UEFI installs, you should not be booting in BIOS mode, it just will not work.
Not sure how sysllnux got installed, but it should not have been. But as long as you do not try to boot in BIOS mode it is ok as it would not be used.

It says grub install worked?
But efibootmgr did not add an entry.

---

### Post by adellis on 2017-03-12
Thanks for the reply.

Drives have not been switched. sdb was always the main drive and sda holds the data.

Think I messed it up by getting boot-repair to restore the MBR when the first repair didn't work.

I removed the boot flags from sdb but boot-repair now says "GPT detected. Please create a BIOS-Boot partition" which I don't think I want to do.

---

### Post by oldfred on 2017-03-12
The bios_grub or BIOS boot partition is for BIOS booting, not UEFI boot.
You do need boot flag on the FAT32 partition sdb1 to make it an ESP.

You system seems to be a bit different than most UEFI.

Is best with UEFI to have all drives as gpt partitioned.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by adellis on 2017-03-12
I was more confortable with old fashioned Linux with LILO and simple partitions. :P

I set the boot flag on sdb1 but it doesn't change anything. See [http://paste.ubuntu.com/24166171/](http://paste.ubuntu.com/24166171/)

---

### Post by oldfred on 2017-03-12
Every system I have seen so far needed an ESP on the sda drive with gpt partitioning.
Not sure how you managed to install to sdb1 and boot?

I would convert sda to gpt and add an ESP. Then reinstall grub using Boot-Repair's advanced mode.
Generally better to have first drive as boot drive and rest as data.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
    
Other NUC needed to boot from the fallback or hard drive entry also. That is /EFI/Boot/bootx64.efi.
       UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)
BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/) 
    
I have instructions on copying /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi in the ESP below in my signature. 
But Boot-Repair now normally does that.

---

### Post by adellis on 2017-03-16
Before I wipe and reinstall the latest server image I thought I'd try to recover the boot partition.

I deleted sdb1, then recreated it and then tried to get boot-repair to fix it. I got mixed messages from boot-repair. First it said I needed a blank partition with boot-grub flag. When I did that it said I needed a FAT32 partition with boot flag. I did that and then forced boot-repair to continue but it still didn't work.

Is it possible to recreate the boot partition from scratch? Or should I just reinstall?

Regards

Adrian

---

### Post by oldfred on 2017-03-16
It needs the bios_grub partition if installing in BIOS boot mode to a gpt partitioned drive.
Boot-Repair's default setting is to install grub to all drives, so then in BIOS mode every gpt drive must have a bios_grub partition.
But that is only if you boot installer in BIOS mode.

If you boot installer in UEFI mode then it must have the ESP - efi system partition. And that normally is on sda. Somehow you had a working one on sdb.
I would expect reinstall of grub in UEFI mode to want the ESP on the sda drive.
But I normally put both the FAT32 ESP and unformatted bios_grub on every gpt drive including my larger flash drives and a data drive. And I now only use gpt. I also typically have a backup bootable install on every drive even if only currently a data drive.

How you boot installer/live media, it then how it installs & default repairs.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by adellis on 2017-03-18
I'm still trying to fix this issue but I think I could have reinstalled by now :p

I converted sda to GPT and created another partition (sda3) at the start that is FAT32 formatted with the boot flag set, then perfomed a boot-repair which looked to be OK, but it still doesn't boot.

Latest boot summary can be found at [URL="http://paste.ubuntu.com/24202904/"]http://paste.ubuntu.com/24202904/

[/URL]There is a warning about Grub2 being installed in the MBR of /dev/sda and it can't find core.img, is there a way to fix this?

---

### Post by oldfred on 2017-03-18
Only if trying to reinstall grub in BIOS mode will you get a complaint about core.img. That has to be in the bios_grub 1 or 2MB unformatted partition.
But if reinstalling or just reinstalling grub in UEFI mode, it should auto install to the ESP - efi system partition on sda.

Be sure to boot in UEFI mode, and use Boot-Repair's advanced mode to totally uninstall and then reinstall grub-efi-amd64.

---

### Post by adellis on 2017-03-19
I've rechecked my settings and legacy (BIOS) boot is not used and secure boot is off.

The system now enters a grub command line from which I can get the system to boot by following the instructions in this thread, [https://ubuntuforums.org/showthread.php?t=1574221](https://ubuntuforums.org/showthread.php?t=1574221)

I just need to get this to work automatically. Running grub-install says no errors reported but I get 
> efibootmgr: Could not set variable Boot0000: No such file or directory
efibootmgr: Could not prepare boot variable: No such file or directory
when executing the "efibootmgr -c -d /dev/sda -p 3 -w -L ubuntu -l \EFI\ubuntu\grubx64.efi

efibootmgr then doesn't show the ubuntu option so I guess the above hasn't worked.

If there a way to fix this now that I can log in?

---

### Post by oldfred on 2017-03-19
I have always used sudo, but otherwise should be ok.

I used this to create the hard drive entry or fallback, after copying shimx64.efi to /EFI/Boot/bootx64.efi

 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  

You have a lot of duplicate entries, you might want to remove some or all of them.
      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

