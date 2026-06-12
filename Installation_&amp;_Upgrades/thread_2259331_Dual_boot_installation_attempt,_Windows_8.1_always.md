---
title: "Dual boot installation attempt, Windows 8.1 always starts"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by miguel33 on 2015-01-03
I have installed latest UbuntuStudio 14.04 on my Toshiba Satellite laptop, I used a partition in the same hd as windows. Installation looked sucessful but I cannot start it. 

I followed instruction from [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and used repair boot automatica repair option, it generated report:

[http://paste.ubuntu.com/9667140/](http://paste.ubuntu.com/9667140/)

I also tried to change the order of the boot manager ```
[COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi[/COLOR]
```


still did not help, I am not sure what else is missing, it seems that boot manager has been changed but I don't see an option booting UbuntuStudio as below:

```
C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\ubuntu\shimx64.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
integrityservices       Enable
default                 {current}
resumeobject            {860ae102-7cf2-11e4-a02e-0071c20f8e26}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 0


Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 8.1
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {af36dba4-7cf2-11e4-8259-0071c20f8e26}
integrityservices       Enable
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {860ae102-7cf2-11e4-a02e-0071c20f8e26}
nx                      OptIn
bootmenupolicy          Standard
```


any advice is very welcome, thanks for your time.

---

### Post by oldfred on 2015-01-04
From either UEFI menu or from f12 can you boot the ubuntu entry?

      ```
**[SIZE=1][FONT=arial]efibootmgr -v[/FONT][/SIZE]**

  BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0005,0003,0001,0002,0000,0004
Boot0000* Windows Boot Manager    HD(2,200800,32000,da9378d7-ebb6-11e3-867e-60029205e206)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI: IP4 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(0071c20f8e26,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(0071c20f8e26,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* UEFI: SAMSUNG MZMTE256HMHP-00000    ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000HD(2,200800,32000,da9378d7-ebb6-11e3-867e-60029205e206)..BO
Boot0004* [COLOR=#ff0000]ubuntu[/COLOR]    HD(2,200800,32000,da9378d7-ebb6-11e3-867e-60029205e206)File(EFIubuntushimx64.efi)
Boot0005* UEFI: TDK LoR TF10 PMAP    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(2,0)HD(1,1f80,39b0880,c3072e18)..BO


```    

What model Toshiba?

Others change /EFI/Boot/bootx64.efi to really be grubx64.efi or shimx64.efi and then can boot a hard drive entry in UEFI. But backup efi partition first. It is not large and can just be copied to another device.

       Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)

Supposedly Windows syncs the BCD with UEFI, so maybe you have to reboot to get it to sync? The sync often overwrites the changing of ubuntu to be first in UEFI boot order. But I would try ubuntu first, hard drive second, Windows third, and the IP network boots last. You may be able to change in your UEFI boot screen or use efibootmgr.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v


 Change boot order with efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
Example 3 is changing boot order:
      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by miguel33 on 2015-01-04
> From either UEFI menu or from f12 can you boot the ubuntu entry?
F12 only allows me to select the device to boot from,  it does shows HDD as an option but not which OS.

> What model Toshiba?
Toshiba Satellite P50-B-10P


> Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)

That worked for me too :), so I will close the thread.

thanks a lot for the support.

---

