---
title: "Dual Booting Windows and ubuntu without having to use GRUB2"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by dnthns87 on 2010-06-13
The Problem, installing ubuntu over top of windows and vice versa causes the windows boot menu to forget about ubuntu.


The Solution:

1. Using bcdedit from within windows to edit the boot menu

Click Start -> Type Cmd.exe run it in elevated mode (as an administrator) by right clicking it and selecting "Run As Administrator" Inside the console type bcdedit, notice that the ubuntu boot entry is still there, for example i use three o/s , windows 7 professional x64, windows 7 ultimate x64 and Kubuntu and it looks like this 


[B]Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {default}
resumeobject            {742ab90c-5f22-11df-9fd2-c2ca2fb681b7}
displayorder            {current}
                        {default}
                        {742ab910-5f22-11df-9fd2-c2ca2fb681b7}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7 Professional x64
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {742ab8fc-5f22-11df-9fd2-c2ca2fb681b7}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {742ab8fa-5f22-11df-9fd2-c2ca2fb681b7}
nx                      OptIn

Windows Boot Loader
-------------------
identifier              {default}
device                  partition=N:
path                    \Windows\system32\winload.exe
description             Windows 7 Ultimate x64
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {742ab90e-5f22-11df-9fd2-c2ca2fb681b7}
recoveryenabled         Yes
osdevice                partition=N:
systemroot              \Windows
resumeobject            {742ab90c-5f22-11df-9fd2-c2ca2fb681b7}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {742ab910-5f22-11df-9fd2-c2ca2fb681b7}
device                  partition=N:
path                    \ubuntu\winboot\wubildr.mbr
description             Kubuntu
[/B]

Next using a program called Vista boot pro 3, will make it easyer for you but create a "New Os Entry" you can do that by opening the program and click "Manage OS Entrys" by clicking the top tab or by manually creating one using bcdedit, As "Os Name" Put Kubuntu, As "Os Type" Select Windows Legacy then select your drive, Select "Apply Updates" And Restart, When you start Notice two entrys called Kubuntu, Boot into kubuntu.. Reboot and Boot back into windows, Open Vista Boot Pro, And remove the new kubuntu entry.

If this does not work, before rebooting use bcdedit to set the path of the new boot entry

---

### Post by darkod on 2010-06-13
This is for using wubi, not full dual boot. And in most cases the wubi entry is added to the windows bootloader automatically without any need for intervention.
Wubi installs never use grub2 anyway.

---

