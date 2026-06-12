---
title: "Toshiba C50 (UEFI) doesn't boot"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by Jesus_Bautista on 2014-12-29
Hi, please I need help!!!

I have just buy a new laptop Toshiba C50, my first idea was install ubuntu and keep W8.1 installed in the laptop, but when I install ubuntu, don't find W8.1 and ask me to erase all the disck. I deacivated fast power-on and boot securryty, but still doasn,t find W8.1

So, I decided erase Windows 8.1 and install only Ubuntu. I install all the sistem and when reboot the sistem say :" Reboot and select proper Boot device..."

I changed boot from USB to HDD, but no way. Then I installed boot-repair and make it work, but it doasn`t repair the problem, pleas check   paste.ubuntu.com/9643219  and tell me what can i do!!!

Thanks!

---

### Post by oldfred on 2014-12-30
Is this it?
[http://paste.ubuntu.com/9643219/](http://paste.ubuntu.com/9643219/)


Toshiba's now also only boot Windows. 
So we have to do a work around and there are several.

You can rename ubuntu to read Windows and UEFI thinks it boots Windows and really boots grub.
Or you can add a /EFI/Boot/bootx64.efi which is a file normally used to boot from hard drive. That still works so we make bootx64.efi really be grub's efi file.

Most of the current known work arounds:
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

You show this:

```
 BootOrder: 0000,0001,0002,0004,0005,000A
Boot0000* ubuntu	HD(1,800,100000,09e51e78-0158-41f6-84c3-bfec526298b4)File(EFIubuntushimx64.efi)


```    

       
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Other Toshiba

 Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
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

---

