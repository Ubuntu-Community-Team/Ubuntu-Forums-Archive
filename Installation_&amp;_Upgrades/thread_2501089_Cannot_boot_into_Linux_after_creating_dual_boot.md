---
title: "Cannot boot into Linux after creating dual boot"
date: 2024-09-22
forum: Installation &amp; Upgrades
---

### Post by floasdffda on 2024-09-22
I created a dual boot from Ubuntu following this guideline: [https://itsfoss.com/install-windows-after-ubuntu-dual-boot/](https://itsfoss.com/install-windows-after-ubuntu-dual-boot/)
Everything worked well but I cannot boot into Ubuntu anymore. It doesnt show in the BIOS. I know the Ubuntu partition still exists with all the booting files. I went into live Ubuntu and tried boot repair. These are my pastebins from before and after the recommended repair:

[https://paste.ubuntu.com/p/mvmP4XBy92/](https://paste.ubuntu.com/p/mvmP4XBy92/)
[https://paste.ubuntu.com/p/p6BXNTvCSp/](https://paste.ubuntu.com/p/p6BXNTvCSp/)

After running the recommend repair, the feedback screen said: Locked NVram detected

I'm using a Lenovo ThinkPad. Please if necessary tell me what information you need to get help.

---

### Post by jeremy31 on 2024-09-22
Can you boot into Windows, open command line with admin privileges and post results for ```
bcdedit /enum firmware
```

---

### Post by floasdffda on 2024-09-22
```
Firmware Boot Manager---------------------
identifier              {fwbootmgr}
displayorder            {bootmgr}
                        {7e3e18b2-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18b3-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18b4-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18b5-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18b6-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18b7-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18b8-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18b9-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18ba-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18bb-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18bc-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18bf-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c0-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c1-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c2-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c3-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c4-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c5-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c6-7856-11ef-879a-cd6a5210a6dd}
                        {7e3e18c7-7856-11ef-879a-cd6a5210a6dd}
timeout                 0


Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {0ea15108-7893-11ef-a3b6-9f09c1fd3136}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b2-7856-11ef-879a-cd6a5210a6dd}
description             Setup


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b3-7856-11ef-879a-cd6a5210a6dd}
description             Boot Menu


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b4-7856-11ef-879a-cd6a5210a6dd}
description             Diagnostic Splash Screen


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b5-7856-11ef-879a-cd6a5210a6dd}
description             Lenovo Diagnostics


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b6-7856-11ef-879a-cd6a5210a6dd}
description             Asset Information


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b7-7856-11ef-879a-cd6a5210a6dd}
description             Regulatory Information


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b8-7856-11ef-879a-cd6a5210a6dd}
description             ThinkShield secure wipe


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18b9-7856-11ef-879a-cd6a5210a6dd}
description             ThinkShield Passwordless Power-On Device Manager


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18ba-7856-11ef-879a-cd6a5210a6dd}
description             Wi-Fi Configuration


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18bb-7856-11ef-879a-cd6a5210a6dd}
description             Reinstall Windows from Cloud


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18bc-7856-11ef-879a-cd6a5210a6dd}
description             Intel(R) MEBx


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18bd-7856-11ef-879a-cd6a5210a6dd}
description             Startup Interrupt Menu


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18be-7856-11ef-879a-cd6a5210a6dd}
description             Rescue and Recovery


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18bf-7856-11ef-879a-cd6a5210a6dd}
description             USB CD


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c0-7856-11ef-879a-cd6a5210a6dd}
description             USB FDD


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c1-7856-11ef-879a-cd6a5210a6dd}
description             NVMe0


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c2-7856-11ef-879a-cd6a5210a6dd}
description             USB HDD


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c3-7856-11ef-879a-cd6a5210a6dd}
description             PXE BOOT


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c4-7856-11ef-879a-cd6a5210a6dd}
description             LENOVO CLOUD


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c5-7856-11ef-879a-cd6a5210a6dd}
description             ON-PREMISE


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c6-7856-11ef-879a-cd6a5210a6dd}
description             Other CD


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c7-7856-11ef-879a-cd6a5210a6dd}
description             Other HDD


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c8-7856-11ef-879a-cd6a5210a6dd}
description             IDER BOOT CDROM


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18c9-7856-11ef-879a-cd6a5210a6dd}
description             IDER BOOT Floppy


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18ca-7856-11ef-879a-cd6a5210a6dd}
description             ATA HDD


Firmware Application (101fffff)
-------------------------------
identifier              {7e3e18cb-7856-11ef-879a-cd6a5210a6dd}
description             ATAPI CD


C:\WINDOWS\system32>
```

---

### Post by jeremy31 on 2024-09-22
Is there any option in BIOS that sounds anything like boot protect?

---

### Post by floasdffda on 2024-09-22
I only found some options about Secure boot but nothing about boot protect. Thank you for helping me.

---

### Post by jeremy31 on 2024-09-22
There was a way to create a new entry in Windows 10 with bcdedit but I can't find the instructions now and the ones I do find aren't working on my Windows 11 machine

---

### Post by oldfred on 2024-09-22
Your Raptor Lake processor is pretty new.
You may need 24.04.1 to have latest kernel & driers to support that new of a system.

---

### Post by jrmsco on 2024-09-25
What was the OS installation order  - Ubuntu first then Windows or Win first then Ubuntu ?
Ubuntu first then Windows doesn't work as windows grabs the boot partition and overwrites any info put there for Linux.
You have to install Windows first and let Ubuntu / grub create the boot menu when it installs.

---

