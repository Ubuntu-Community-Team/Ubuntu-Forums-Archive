---
title: "UEFI Boot-Repair Sony"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by chdimosthenis on 2015-12-21
I had a pretty similar case with boot-repair, where the purge kernels option left my operating system with no ubuntu option in GRUB.

This is the [paste]("http://paste2.org/GEKLAghz") output from the LiveUSB, because booting into the system is not an option now.

Any thoughts on that? I should have propably waited for the procedure of purging and reinstalling to end, rather than to act dumbly and manually terminate and get finally locked out of my environment.

---

### Post by oldfred on 2015-12-21
Moved to your own thread. I also saw Sony?

You do have to let Boot-Repair's updates finish, or else you do not have a correctly configured system. It does need working Internet to download new copy of grub & kernels.

You also show a Sony? 

Boot-Repair says you have secure boot on, best to turn it off.
Sony will not boot ubuntu entry in UEFI. The violate UEFI specifications.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

            One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

---

