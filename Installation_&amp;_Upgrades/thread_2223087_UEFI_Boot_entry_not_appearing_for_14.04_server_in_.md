---
title: "UEFI Boot entry not appearing for 14.04 server in NVMe device"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by arka.sharma on 2014-05-09
Hi All,

I have successfully installed Ubuntu 14.04 in NVMe device on Dell Poweredge R820 server and Intel Desktop Board with Visual BIOS. In both the cases installation completes but in the UEFI boot entry "ubuntu" doesn't get listed. However in both the cases booting from shell by invoking "grubx64.efi" is working. I have cross checked the same with SAS disk in the server and with a SATA SSD in desktop and in both the cases boot entry in being listed. I booted to shell from a usb drive and foubd in all the cases grubx64.efi in the same path "fsX:\EFI\ubuntu\grubx64.efi". But only in case of NVMe device boot entry is not being listed. So I copied the "grubx64.efi" to "fsX:\EFI\boot\bootx64.efi" which is adding a boot entry in both server and the desktop UEFI boot menu and it is booting also. However this boot entry doesn't show as "ubuntu" it list as "UEFI Os loader" in the desktop boot menu and "PCIe Solid State Drive (and slot no )" in the server.I am wondering why only in case of NVMe device boot entry are not coming properly. Even though it is working but it will be of great help if anyone can share some suggestion."

Thanks & Regards,
Arka

---

### Post by oldfred on 2014-05-09
I do not know servers.

But many with Windows systems have to move grub or shim to the /boot efi folder and that is the drive entry in UEFI menu. I would think it should show the ubuntu entry.

What does this show?
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm them.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

---

### Post by arka.sharma on 2014-05-12
Thanks for your reply. I installed Ubuntu 14.04 in Asus P8Z68 Deluxe system where "ubuntu" boot entry is appearing and booting without any problem. I booted to ubuntu and issue "efibootmgr -v" and in the Dell server as well. The difference I found in the output is in Asus system the boot entry is pointing to "File(EFI\ubuntu\grubx64.efi)" and in the server the boot entry corresponding to ubuntu(which is grayed out) is showing "File(\EFI\ubuntu\shimx64.efi)". Could this be a reason ?

---

### Post by oldfred on 2014-05-12
Shim is the secure boot version of grub. I thought they were going to standardize on just using shim for all systems, but still see every sytem with both.

Often systems show two UEFI ubuntu entries one shim & one grub.
When secure boot is on only shim will show.

If grayed out are you in BIOS mode, or is secure boot on and it does not think it is the signed software?

---

### Post by ubfan1 on 2014-05-12
Shim is just a very simple program (seldom/never needing updates) to run the grub version signed by Canonical.  Canonical pays Microsoft to sign shim so it can run under secure boot.  Since every grub change would require a new payment to Microsoft, I doubt they will ever be combined. 
  It is a good idea to set up a parallel boot mechanism (the first in /EFI/ubuntu) in /EFI/Boot.  For secure boot, the /EFI/Boot/bootx64.efi file should be a copy of shim.efi, and a copy of the signed grubx64.efi needs to be present too (the grub.cfg file will still be picked up from /EFI/ubuntu).  For non-secure boot, you could just use the unsigned copy of grubx64.efi for bootx64.efi (but the secure setup will still work in this case also).  The /EFI/Boot  files may be a silent fallback in case the original boot fails for some reason (like an unwanted nvram change, which seems all too common).

---

### Post by arka.sharma on 2014-07-14
Hi,

I have installed Ubuntu 14.04 desktop in UEFI mode on Intel haswell system. Here I am observing that boot entry is being created as "Ubuntu" but while selecting it to boot is causing boot failure and coming back to UEFI BIOS setup. Now if I change the EFI\Ubuntu\grubx64.efi to EFI\Boot\Bootx64.efi from shell then it is booting. Alternatively if I create a new boot entry pointing to EFI\Ubuntu\grubx64.efi then also booting is working. As I have mentioned earlier this problem is not seen Asus Z87 and Asus P8 series system. After doing some searching I found that similar issue has been seen in DELL servers with Suse Linux [ftp://ftp.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_operating_system/novl-suse-lx-entps-srvr-11_User%27s%20Guide_en-us.pdf](ftp://ftp.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_operating_system/novl-suse-lx-entps-srvr-11_User%27s%20Guide_en-us.pdf) and as per the cause mentioned in the document is "**This is caused due to the way Linux creates the GUID Partition Table (GPT) partition**.". But I want to add that this issue on haswell system I have seen with NVMe device. When I install Ubuntu 14.04 in UEFI mode in an AHCI device this issue is not coming, I mean it directly boots to Ubuntu without any workaround. Also like I have mentioned already when I install Ubuntu 14.04 in UEFI mode in NVMe device on Asus Z87 system that also boot to Ubuntu without any manual intervention. I just want to know what exactly is causing this issue. Also Linux doesn't create usual /dev/sd* for NVMe device. NVMe devices are listed as /dev/nvme0n1 and the partitions are as /dev/nvme0n1p1,/dev/nvme0n1p2 and so on. But if it is a problem with Ubuntu itself how come the same is working on Asus system ? Is there any issue in UEFI setup also ?

Regards,
Arka

---

### Post by oldfred on 2014-07-14
I did not know any Z87 systems supported NVMe  devices. There was an article somewhere that I saw the first motherboard with support for NVMe  was a new z97 motherboard. Was UEFI/BIOS updated to provide support for NVMe devices?

Since NVMe devices are very new that may be an issue. I might file a bug report just to see what developers say. They do not generally post in the forums.

Never heard of any issue with gpt and Linux systems. I have used gpt on older systems without issue. And I do not know if that is really a vendor issue or SuSe issue?

A lot of vendors have modified desktop systems to only boot Windows or only boot UEFI entries with Windows in the description.

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by arka.sharma on 2014-07-15
Actually the NVMe device I am using is a PCIe SSD and contains Option ROM to be able to boot in Z87 pc's. Can you please refer some links where it says Z97 supports NVMe devices. Does that mean Option ROM is not needed in order to boot in Z97 systems ?
Also 
> A lot of vendors have modified desktop systems to only boot Windows or only boot UEFI entries with Windows in the description.

Even if vendors do such customization should not it be applicable regardless the type of storage(AHCI or NVMe etc) devices being used ?
But as per my observation I am facing this issue with haswell board only in NVMe devices(in the same board Windows works fine on the same NVMe device. AHCI device doesn't give this problem.

---

### Post by oldfred on 2014-07-15
I do not really know all this, but this article discussed some of it.
[http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826-9.html](http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826-9.html)

---

