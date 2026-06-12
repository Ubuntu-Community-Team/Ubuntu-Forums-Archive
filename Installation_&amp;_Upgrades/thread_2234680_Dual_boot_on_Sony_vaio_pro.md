---
title: "Dual boot on Sony vaio pro"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by ashish8 on 2014-07-16
Hi 

I have Sony vaio laptop (SVP1321XPNB) with preinstall windows 8.1 (UEFI, secure boot). I am trying to install ubuntu 14.04 in dual boot mode. I followed the given instructions on ubuntu community and other places also
([http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) ,
[http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/),

 then run boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)). But got a message that it encounter with some error and paste link is here [http://paste2.org/ZGCKcBPb](http://paste2.org/ZGCKcBPb) .

I am not able to boot in ubuntu by any means i used all option like boot-repair, using bcdedit , disable fast boot & secure boot. 


   Please suggest me , How do i fix this.




Regards

---

### Post by kc1di on 2014-07-16
If all else fails you may want to consider refind boot loader. it works pretty well with most systems
you can find it[ here.]("http://www.rodsbooks.com/refind/")

---

### Post by oldfred on 2014-07-16
Boot-Repair seems to pick up a minor error somewhere and reports that.

But grub itself correctly installed as 0 exit code is no error:
>  Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0



But Sony has modified UEFI to only boot Windows.
Most user find that renaming bootx64.efi works the best. And some like rEFInd as kc1di suggests.

       One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)


  HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)

---

