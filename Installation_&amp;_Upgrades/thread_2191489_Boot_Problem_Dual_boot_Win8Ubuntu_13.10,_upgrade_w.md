---
title: "Boot Problem: Dual boot Win8/Ubuntu 13.10, upgrade windows 8.1, cannot access Windows"
date: 2013-12-03
forum: Installation &amp; Upgrades
---

### Post by matthew.f.fox on 2013-12-03
I have a Lenovo U410 which was working fine with a dual boot set up, with Windows 8 and Ubuntu 13.10 from the grub2 menu. I upgraded from Windows 8 to 8.1, and now cannot access Windows from grub. I also cannot get to the BIOS to change settings such as secure boot; I only have grub. When I try to access Windows, I get the error: "Secure Boot: Image failed to verify with *access denied* [ok] to continue". When I continue, I get back to grub2 and then can access Ubuntu just fine. 

gparted indicates that the windows 8 partition is intact.
I ran Boot Repair and the problem remains. The information from boot repair is as follows -[URL="http://paste.ubuntu.com/6512763/"]

 http://paste.ubuntu.com/6512763/[/URL]

Any suggestions? Thanks

---

### Post by oldfred on 2013-12-03
Boot-Repair did the 'buggy' UEFI rename. Did you do that before updating Windows?
If so grub then is trying to boot the original Windows 8 bootmgfw.efi not the new one.

Were you able to boot from UEFI entry to ubuntu or only Windows? The rename is only required if you cannot boot ubuntu entry in UEFI menu. Some UEFI only boot the Windows file.

Normally you could do this, but the backups probably are the old versions.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

I would fully backup efi partition as it is now, just in case.

If you can directly boot the ubuntu entry in Windows, just copy the new Windows efi file into your efi partition.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

      This is what Boot-Repair's rename did:
 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

If you can only boot Windows then manually copy the new bootmgfw.efi from c: to /EFI/Microsoft/Boot, but overwrite the existing bkpbootmgfw.efi. 
If you can boot ubuntu from UEFI then you can delete the bkpbootmgfw.efi, and overwrite the bootmgfw.efi (which currently is shim). You will also have to update 25_custom entry from bkpbootmgfw.efi to bootmgfw.efi.

      
 sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
#Then do:
sudo update-grub

---

### Post by matthew.f.fox on 2013-12-04
Thanks for the advice - I restored the EFI backups using Boot Repair. I still am only able to access grub and then Ubuntu. If I choose Windows in grub, I still get the error "Secure Boot: Image failed to verify with *access denied* [ok] to continue".  I cannot access BIOS. I tried booting off of a CD, and the DVD player runs, but the CD does not start, I am taken to the grub menu. With this situation, I am unable to even use recovery disks, because the disks won't run on startup, and the problem persists.

---

### Post by oldfred on 2013-12-04
It sounds like your Windows now only works with secure boot on.
If you turn secure boot on, can you directly from UEFI menu boot Windows, it will only work if the rename has been undone.
If you boot Boot-Repair in secure boot mode, you can upgrade grub & kernel to secure boot signed versions.

---

### Post by matthew.f.fox on 2013-12-05
The Windows does not work at all, I have no access to the BIOS to turn secure boot on or off, only access to the GRUB menu, which only allows me to load Ubuntu. It appears that secure boot is on, and I am unable to access the UEFI menu, only grub. At this point, I would be happy with abandoning my effort to restore access to my Windows OS, and instead shrink or delete that partition and expand the Ubuntu partition, unfortunately I only have access to GRUB on start up / reboot of the computer.

---

### Post by oldfred on 2013-12-05
I believe grub or Boot-Repair is adding an entry to get you directly to UEFI. It should be the last entry in the menu?
Do you have that entry?

---

### Post by matthew.f.fox on 2013-12-05
Thanks, you are correct, I have that entry in GRUB to the UEFI, as well as UEFI recovery. Both of them give the error: cannot load image.

---

### Post by oldfred on 2013-12-05
Some other possibly related threads.

 Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.
      
 Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)

---

### Post by matthew.f.fox on 2013-12-15
Thanks oldfred, I still haven't resolved the issue, but following the links you provided led me to posts by others with apparently the same issue. I think this is bug 1091464, documented at [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

