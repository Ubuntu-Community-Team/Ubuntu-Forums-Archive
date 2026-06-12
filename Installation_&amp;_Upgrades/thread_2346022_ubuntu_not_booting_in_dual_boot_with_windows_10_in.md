---
title: "ubuntu not booting in dual boot with windows 10 in Uefi mode"
date: 2016-12-10
forum: Installation &amp; Upgrades
---

### Post by minodev on 2016-12-10
Hello everyone,

I have a laptop with a pre-installed Windows 10. I wanted to switch to ubuntu, but I decided to leave windows installed in case ubuntu's installation doesn't work. So I created a **new partition** and installed **ubuntu 16 LTS **on it in **uefi mode**, using a live USB made by Rufus.
Ubuntu was installed successfully and restarted. But **Windows quickly loaded as if nothing happened**. And **I can't access Ubuntu**. Even by holding Shift+Restart and chosing Ubuntu.

I tried every solution I found especially those mentionned in :
[LIST]
[*][http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
[*][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[/LIST]

I used the command **bcdedit **to set the path to ubuntu 
```
C:\WINDOWS\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
path                   ** \EFI\ubuntu\shimx64.efi**
description             Windows Boot Manager
locale                  en-GB
inherit                 {globalsettings}
default                 {current}
resumeobject            {11e89e34-0792-11e6-bec9-91b447580268}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30


Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \WINDOWS\system32\winload.efi
description             Windows 10
locale                  en-GB
inherit                 {bootloadersettings}
recoverysequence        {11e89e36-0792-11e6-bec9-91b447580268}
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \WINDOWS
resumeobject            {11e89e34-0792-11e6-bec9-91b447580268}
nx                      OptIn
bootmenupolicy          Standard
```

I started Live CD version of ubuntu to copy **shimx64.efi** to **/EFI/Boot** and **/EFI/Microsoft/Boot** and renamed it to** Bootx64.efi** and **Bootmgfw.efi** using a Terminal. And when I restarted, nothing happened and I got this error :

```
Insert system disk in drive,
Press any key when ready....
``` 

Then I restored back the boot files, and retried with** Boot-Repair'**s recommended repair. Restarted, and I got the same previous error...

I also can't choose ubuntu to boot first from **Uefi boot in bios setting**, as I find only  HDD/SSD, USB memory, ODD, LAN1, LAN2 ....
Same when executing the command **efibootmgr **[COLOR=#111111][FONT=Consolas].[/FONT][/COLOR]


Please help me. I wasted an entire day trying differents solutions as nothing seem to work out for me.

[B]Computer infos:

[/B]**Toshiba Portege R930 **series
Os : Windows 10
**UEFI boot** with **secure boot**
**Intel Rapid Start**
**SSD 256 Go**

---

### Post by oldfred on 2016-12-10
You do not want to rename /EFI/Microsoft/Boot/bootmgfw.efi.
That process was used when other work arounds were not known. But then you could only boot Windows from a grub entry using the renamed file. And Windows updates overwrote it anyway.

Most systems do work with the fallback entry of /EFI/Boot/bootx64.efi making that file really be shimx64.efi and booting from UEFI a hard drive boot entry that boots /EFI/Boot/bootx64.efi.

Most that have these issues will never boot the ubuntu entry in UEFI. They have modified UEFI to boot using description which is specifically not allowed in UEFI spec. But fallback or hard drive boot entry still works. If you have the bootx64.efi file that is a just a copy of the Windows bootmgfw.efi file. Boot-Repair will copy bootx64.efi to a backup and copy shimx64.efi if you check "use the standard efi file" in advanced mode.
But you may need UEFI entry to boot fallback or hard drive entry.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Older threads, users manually copied shim as Boot-Repair did not then do the copy.
      
 Toshiba Satellite - turned Secure boot off in Boot-Repair update
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[URL="http://ubuntuforums.org/showthread.php?t=2247186"]http://ubuntuforums.org/showthread.php?t=2247186
[/URL]Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061) [URL="http://ubuntuforums.org/showthread.php?t=2247186"]
[/URL]

---

### Post by minodev on 2016-12-12
Thank you a lot for your help. Unchecking "Secure boot" in Boot-Repair before starting the repair and disabling Secure boot in my Bios settings made Grub show up thus allowed me to access both installed Ubuntu and Windows 10. 
This was partially mentioned in : 

> **oldfred said:**
> 
 Toshiba Satellite - turned Secure boot off in Boot-Repair update
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)[URL="http://ubuntuforums.org/showthread.php?t=2247186"]
[/URL]

Thank you again.

---

