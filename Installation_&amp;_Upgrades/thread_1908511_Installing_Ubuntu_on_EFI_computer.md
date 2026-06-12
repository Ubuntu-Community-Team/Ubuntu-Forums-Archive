---
title: "Installing Ubuntu on EFI computer"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2012-01-13
Hi
i'm trying to help a user who has tried to install Ubuntu in dual-boot with Windows on a EFI computer. But this case is difficult and i need your help.

The default installation failed (no access to Ubuntu), and broke access to Windows.

Here is the Boot-Info-Script summary : 
- stable: [http://paste.ubuntu.com/803082](http://paste.ubuntu.com/803082)
- GIT version: [http://paste.ubuntu.com/803319/](http://paste.ubuntu.com/803319/)

Boot-Repair detected that :
- Ubiquity installed grub-efi
- boot is in EFI mode
- there is no EFI partition
- the partition table is MS-Dos type


What would you recommend ?  (installing grub-pc ?)

---

### Post by oldfred on 2012-01-13
It looks like the grub in the MBR of sda is looking for sda11, but the install is in sda13. But normally there would be a core.img in sda13 also but it is missing so the grub install may not be correct. A reinstall of the grub2 boot loader to the MBR may fix it, but not sure how core.img gets into both the area after the MBR & in the partition.

Boot flag on sda7 does not mean anything. Windows has to have a boot flag on a primary and Linux does not need one (unless using Lilo). Needs to be on Windows boot partition if repairs required also.

Looks like a lot of copied Windows partitions as NTFS boot sectors are confused about size or location. NTFS boot sectors have to match partition table.

Windows will only boot in UEFI mode if drive is gpt and first partition is efi.

Grub boots from gpt or MBR from BIOS or UEFI with gpt (maybe even MBR & UEFI but that would be non-standard).

It only looks like the syslinux on the 4GB flash drive as UEFI in a efi partition.

If Ubuntu sees a empty drive over 1TB it will format to gpt mode. Not sure how it knows if UEFI or BIOS.

---

### Post by YannBuntu on 2012-01-13
AFAIK:
1) this computer boots in EFI mode (Boot-Repair detects it via the "dmesg | grep EFI | grep -v "Variables Facility" command)
2) the Ubuntu installer used grub-efi (we can see it's grub-efi because of the "insmod efi_gop" , and "insmod efi_uga" in the grub.cfg . I guess it's because the Ubuntu installer detected that boot is EFI mode (see previous point) 
3) grub-efi does not install core.img in /boot/grub , but in the EFI partition. For this user, that explains that there is no core.img in sda13 , but i don't know where core.img has gone ... maybe the Ubuntu installer tried to install EFI files in sda1 , which would explain why Windows boot in now broken.

What i would suggest to this user is:
- first repair the Windows boot via a Windows Recovery disk
- then reinstall GRUB2, but this time via grub-pc , not grub-efi

do you think it's the best solution ?

---

### Post by oldfred on 2012-01-13
I think to repair Windows the boot flag will have to be back on the Windows partition, otherwise Windows does not even see its own boot partition.

Windows & drive are MBR, so Ubuntu should not have used efi mode. But then grub has several bugs. 

If it is not this one then the OP should post a new one. They do not seem to work on bugs until several confirm it, so it would be good to add to the list of those with the problem and details.
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

### Post by YannBuntu on 2012-01-13
The disk is MBR-type and Windows seems normal (not EFI), which looks classic, and generally requires grub-pc.

BUT on the other side this computer uses an EFI session by default (although there is no GPT), and i think this is why Ubiquity mistook and installed grub-efi instead of grub-pc. I will fill a bug report against "ubiquity". EDIT: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/916299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/916299)

So I will recommend this user to reinstall grub-pc in sda and update.
GRUB should appear.
After this, if Ubuntu boots but Windows is still broken:
1) move the boot flag to sda1
2) repair Windows boot with Windows Recovery CD
3) reinstall grub-pc in sda

---

