---
title: "No dual boot on Sony VAIO SVS1311F3EW"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by riccardo10 on 2015-10-18
Hi all,

I've tried both installing first Windows 10 and then Ubuntu 14.04 and viceversa, first Ubuntu then Windows.

What happens is that both cases, is that it only boots Windows 10 and never show any sign of ubuntu. 

I've tried boot repair in both cases in the EFI partition with no success.
[SIZE=2]http://paste.ubuntu.com/12816230/

[SIZE=2]http://paste.ubuntu.com/12840671/
[/SIZE]
I've even tried changing from Windows the path with bcdedit to EFI\ubuntu\ with no success...

How can I fix the dual boot?

Cheers, 
Riccardo.



[/SIZE]

---

### Post by oldfred on 2015-10-18
I think evey Sony we have seen will not directly boot Ubuntu.
They modify UEFI to also use description which is not allowed in UEFI spec.
And the description must be "Windows".
But UEFI has a backup hard drive boot entry and with Sony that entry will usually work.

You have to copy /EFI/ubuntu into /EFI/boot and rename shimx64.efi to bootx64.efi. And then add an UEFI boot entry for the hard drive.

Details, also in link in my signature:
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

    
       One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

            Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)

---

