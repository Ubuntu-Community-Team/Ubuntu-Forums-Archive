---
title: "Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50)"
date: 2014-12-18
forum: Installation &amp; Upgrades
---

### Post by taserian on 2014-12-18
After trying Boot-Repair, I'm still unable to get GRUB to show, or boot into Ubuntu.

Boot-Repair provided the following URL:
[http://paste.ubuntu.com/9559987](http://paste.ubuntu.com/9559987)

Can anyone provide some help?

AR

---

### Post by yancek on 2014-12-18
So what exactly happens?  Do you see boot options or a menu?  Did you try the suggestions in the last paragraph of the boot repair text?

---

### Post by oldfred on 2014-12-18
Others with Toshiba said they had to copy the grub files in the /EFI/ubuntu/grub folder into the /EFI/Boot folder. Backup bootx64.efi or rename it, as it is a hard drive boot entry. And rename grub or shim to be bootx64.efi. Then the hard drive boot entry in UEFI boot menu really boots grub.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
    
 From live installer mount the efi partition on hard drive:
mount /dev/sda2 /mnt
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

Several other Toshiba users and several other issues. 
 [SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by taserian on 2014-12-24
Apologies for not providing more details sooner. I was on my way out to work when I posted, then I was in the hospital for food poisoning! Thankfully, oldfred's answers got me through getting GRUB working, and now I have Ubuntu and Windows 8 on side-by-side. Thanks for your interest!

---

### Post by taserian on 2014-12-24
Many thanks! Your instructions were perfect! Sorry I didn't answer sooner; I've been in the hospital for food poisoning, and only got back home recently.

---

### Post by oldfred on 2014-12-24
Glad you are feeling better. 
And that system is working.

Please post solved, instructions in signature below, if needed.
Then others can search forum and find a working solution.

---

