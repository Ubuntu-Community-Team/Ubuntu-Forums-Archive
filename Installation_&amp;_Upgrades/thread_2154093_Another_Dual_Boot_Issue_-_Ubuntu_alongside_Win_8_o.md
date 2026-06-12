---
title: "Another Dual Boot Issue - Ubuntu alongside Win 8 on Lenovo"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by marcjb on 2013-06-13
Hello,
I just installed Ubuntu alongside Windows 8 on a new laptop, and I now cannot boot Windows 8
[http://paste.ubuntu.com/5761719/](http://paste.ubuntu.com/5761719/)

I've tried a number of the solutions posted online (including manually editing the 40_custom file, boot repair, etc), but I still can't get a normal Windows 8 boot (only the recovery UEFI ones work).  I have secure boot off, and I used one of the recovery win boots to ensure that Fast Startup was disabled.  I appreciate any help you can give.

Thank you,

Marc

---

### Post by ubfan1 on 2013-06-13
Machines with preinstalled Windows 8 are supposed to only boot Windows if secure boot is on.   If you installed Ubuntu with secure boot off, you got the unsigned version of the Ubuntu grubx64.efi for your bootloader, which won't boot with secure boot on.  I think boot-repair will fix this if run with secure boot on.  Before boot-repair renamed the boot files, your efi boot menu (chose device hdd, then os) would skip grub and still boot windows, but the boot-repair function "restore backup files" should put things back to the original state (which may work fine for you).  Each machine is different, so search this forum for Levono UEFI or secure to see  more specific information.

---

### Post by marcjb on 2013-06-13
> **ubfan1 said:**
> Machines with preinstalled Windows 8 are supposed to only boot Windows if secure boot is on.   If you installed Ubuntu with secure boot off, you got the unsigned version of the Ubuntu grubx64.efi for your bootloader, which won't boot with secure boot on.  I think boot-repair will fix this if run with secure boot on.  Before boot-repair renamed the boot files, your efi boot menu (chose device hdd, then os) would skip grub and still boot windows, but the boot-repair function "restore backup files" should put things back to the original state (which may work fine for you).  Each machine is different, so search this forum for Levono UEFI or secure to see  more specific information.

Thank you for the response, ubfan1.  If I turn on secure boot, Ubuntu won't load, so I cannot run boot-repair.  Also, Windows will not boot either in the secure mode.  I have tried boot-repair with secure boot off, but that is not helping.

Marc

---

### Post by oldfred on 2013-06-13
Some system will boot Windows with secure boot off. Many only boot with secure boot on and many also only boot the Windows efi file. But Boot-Repair will rename grub's shim which has the Microsoft key to then boot grub and from grub boot Windows.

It looks like Boot-Repair has already done the rename.

Have you done this from Boot-repair?
 Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

Which Windows entry are you trying to boot with?

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bkpbootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

Your system has the official efi files in sda2, but your vendor has also put other efi files (recover?) into sda3. Boot-Repair adds boot entries for both. But to boot Windows you need the file in sda2. And it looks like Boot-Repair included recovery in the name of all of them (incorrectly).

      
>  /dev/[COLOR=#ff0000]sda2 [/COLOR]      2,050,048     2,582,527       532,480 [COLOR=#ff0000]EFI System partition[/COLOR]
/dev/sda3       2,582,528     4,630,527     2,048,000 -

   /dev[COLOR=#ff0000]/sda2[/COLOR]        [COLOR=#ff0000]D037-FD79[/COLOR]                              vfat       SYSTEM_DRV
/dev/sda3        8C38-E014                              vfat       LRS_ESP

   Use e in grub menut to confirm UUID, and these should not say recovery, they are the third & 4th Windows entries.
menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]D037-FD79[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

   menuentry "Windows Boot UEFI recovery sda2" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]D037-FD79[/COLOR]
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}




See also my signature for more UEFI info.

---

### Post by ubfan1 on 2013-06-13
As for the chicken-and-egg problem, after you turn secure boot on in the UEFI/BIOS settings, boot from the install media and run boot-repair with the suggested command.

---

### Post by marcjb on 2013-06-14
> **oldfred said:**
> Some system will boot Windows with secure boot off. Many only boot with secure boot on and many also only boot the Windows efi file. But Boot-Repair will rename grub's shim which has the Microsoft key to then boot grub and from grub boot Windows.

It looks like Boot-Repair has already done the rename.

Have you done this from Boot-repair?
 Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

Which Windows entry are you trying to boot with?

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bkpbootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

Your system has the official efi files in sda2, but your vendor has also put other efi files (recover?) into sda3. Boot-Repair adds boot entries for both. But to boot Windows you need the file in sda2. And it looks like Boot-Repair included recovery in the name of all of them (incorrectly).

      



See also my signature for more UEFI info.

Thank you, oldfred.  Late last night, before seeing these comments, I tried the 'rEFInd' Boot Manager, and that worked.  I'm going to look into your suggestion so that I don't need that extra layer.

Marc

---

### Post by marcjb on 2013-06-14
Thank you, ubfan1.  I did get booting to work with 'rEFInd' Boot Manager, but I will try this to see if I can get all the boots to work from one screen.

Marc

---

### Post by oldfred on 2013-06-14
Refind is a Boot manager. It does add nice icons to use to boot from and some prefer that to just grub text.
Post how you got Refind working. 

It was my understanding the current Ubuntu shim may not work with Refind?

 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards]("https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards")
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
More info on secure boot - Ubuntu's shim may need changing to work with Refind
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by marcjb on 2013-06-14
Hey oldfred - thanks!

Looks like you were spot on that the recovery entry was the correct entry to boot with, just had the wrong name.  I removed rEFInd for now, as I can boot from grub.  I may still try ubfan1's suggestion if I want to enable secure boot.

Thanks guys,

Marc

---

### Post by oldfred on 2013-06-14
If you can boot Windows with secure boot off, you may be able to undo the rename of the Windows boot file that Boot-repair did.

You can also edit 25_custom to only have the entries you want and remove the recover text from the working entries.

Details in link in my signature on efi menu cleanup.

---

