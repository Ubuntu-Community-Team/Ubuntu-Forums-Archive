---
title: "cant boot even after boot-repair"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by apollo4 on 2015-04-16
I tried to erase my fujitsu lifebook to install ubuntu 14.04 but cant boot after installation and boot-repair
url after boot-repair

**paste.ubuntu.com/**10832133
[http://paste.ubuntu.com/10832133/](http://paste.ubuntu.com/10832133/)

Thank in advance

---

### Post by apollo4 on 2015-04-16
I suspect my installation is in uefi and my laptop does not support uefi boot.
What should I do to make a legacy installation ?

---

### Post by oldfred on 2015-04-16
Your system is UEFI and Ubuntu is installed in UEFI boot mode.

If you look at line 512 you see all the UEFI boot options. 

The last two in list:
      ```
 Boot000C  Windows Boot Manager	HD(1,800,32000,efde51da-b6ae-4b2a-a739-2836ae43ef10)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot000D* ubuntu	HD(1,800,100000,fcf43ffa-41e7-40a6-b174-db5c09944056)File(EFIubuntushimx64.efi)


```    

First fully backup entire efi partition to another drive or device. You can use Ubuntu live installer in live mode and just use Nautilus file manager.

Some vendors will not let you boot any entry other than the Windows one. And since you only have ubuntu, we can delete the Windows entry and you must also delete the /EFI/Microsoft folder in the efi partition, or else it will get added again to UEFI.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

      
  Use efibootmgr if only Ubuntu, not dual boot, install to make Windows UEFI description boot grub or shim file
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

If you have Windows to restore Windows boot entry:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"


 Some systems require password to turn off UEFI, never ever lose password.
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

---

### Post by grahammechanical on 2015-04-16
You have confused me.

My motherboard dates to a time before UEFI and I do several installations of different versions of Ubuntu every six months and none of them has ever installed in EFI mode because the motherboard does not support it. So, I do not understand how Ubuntu could install on your machine in EFI mode if the motherboard of your machine does not support it.

It is my understanding that if the motherboard boot system is set to EFI mode then we must install Ubuntu in EFI mode and if the boot system is set to legacy or BIOS mode then we must install Ubuntu in legacy mode. 

If Ubuntu or Windows for that matter is installed in EFI mode then switching the boot system to legacy will stop the OS from loading. If the OS is installed in legacy mode then switching to EFI mode will stop the OS from loading.

This is my understanding.

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by apollo4 on 2015-04-17
Still cant boot. It complain message below

Could not open"EFI\BOOT\fallback.efi" :14
Failed to open "EFI\BOOT\grubx64.efi" -800000000000E
Failed to load image
Failed to open "EFI\BOOT\Mokmanager.efi" -8000000000000E
Failed to load image


The files however is exists at "EFI/ubuntu/*"

---

### Post by apollo4 on 2015-04-17
Managed to get to grub after I copy over the files to BOOT dir
Not sure if this is the correct way.
Anyway my issue solved :)
Thanks for all the helps

---

### Post by oldfred on 2015-04-17
That is one of the work arounds for systems that have modified UEFI. And the UEFI standard specifically says they should not make those modifications.

Some also had to copy grubx64.efi to fallback.efi. It seems your system is just using /EFI/Boot and not /EFI/ubuntu like it should.

---

