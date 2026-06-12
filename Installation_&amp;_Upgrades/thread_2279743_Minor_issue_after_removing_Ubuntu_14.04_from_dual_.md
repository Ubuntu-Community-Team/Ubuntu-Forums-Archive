---
title: "Minor issue after removing Ubuntu 14.04 from dual boot"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by linux2000 on 2015-05-25
I have a minor issue after successfully removing Ubuntu 14.04 from dual boot windows 8.1. When I reboot, it directly takes me to windows but when i go into BIOS, there is still Ubuntu as my second os under the boot options. I already tried to fix it by using windows installation media and running bootrec.exe /fixmbr but no effect. If I select Ubuntu inside BIOS, it takes me to grub command prompt. I even tried to delete that from the boot sequence but then when I restart it comes back. How can I get rid of Ubuntu bootloader?
Thanks in advance.
L2k

---

### Post by ubfan1 on 2015-05-25
If your machine came with Windows 8.1 preinstalled, you have a UEFI machine, so the Ubuntu bootloaders are sitting in the EFI partition in the directory /EFI/ubuntu.  They are just files, so mount the partition and delete them.  Also check in /EFI/Boot and see if you have a copy of grubx64.efi sitting there (delete it).  Check the size of /EFI/Boot/bootx64.efi to make sure it's not the same size as grubx64.efi or shimx64.efi (if so, replace it with a copy of /EFI/Microsoft/Boot/bootmgfw.efi).  That totally removes all the Ubuntu bootloaders.
  You will STILL have the nvram entry pointing to the removed bootloaders.  I know efibootmgr on the Ubuntu side (run live media?) can delete nvram entries, there must be some way in Windows too, but I don't know about it.   bootrec.exe /fixmbr ??? You should read about UEFI, there is no longer any "Master Boot Block/record":
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by linux2000 on 2015-05-26
Perfect! I followed your steps and managed to delete the Ubuntu bootloader on my [COLOR=#000000]/EFI and its gone now. Thanks a lot.[/COLOR]

---

