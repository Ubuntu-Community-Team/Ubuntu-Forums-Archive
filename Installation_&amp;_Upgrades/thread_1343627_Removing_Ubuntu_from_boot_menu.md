---
title: "Removing Ubuntu from boot menu"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by bayoubadboy on 2009-12-02
I have Windows 7 and I installed Ubuntu as an application in Windows 7. When I rebooted of course I was presented with the dual boot option. I decided that I wanted to install a full install of Ubuntu on a separate partition on my hard drive, so I deleted the Ubuntu directory folder from my Windows 7 GUI. Now when I reboot, the Ubuntu is still showing in the boot screen and I want to get that removed before I do any further installation. I have been through the bcdedit in the command prompt, but the only thing that ever comes back is:

C:\Windows\system32>bcdedit /delete ba50fdc0-df08-11de-8f8a-f2e85f9e3e44 /f
The specified entry identifier is not valid.
The parameter is incorrect.

But when I do run just the bcdedit at the C: prompt, it does show the Ubuntu as seen here:

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {ede47f60-d335-11de-aad0-be01bf55c5f9}
displayorder            {current}
                        {ba50fdc0-df08-11de-8f8a-f2e85f9e3e44}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {ede47f62-d335-11de-aad0-be01bf55c5f9}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {ede47f60-d335-11de-aad0-be01bf55c5f9}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {ba50fdc0-df08-11de-8f8a-f2e85f9e3e44}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

If someone could just tell me how to have that removed please, I would greatly appreciate the help.

---

### Post by ubestos on 2009-12-02
have you try first to **backup** your configuration?

```
bcdedit /? /export
```
to see what win says about this...
```
bcdedit /export C:\BCDbak
```
now I eported the configuration.
```
bcdedit /import C:\BCDbak /clean
```
... and imported

Then I would try with:

```
bcdedit /delete {ba50fdc0-df08-11de-8f8a-f2e85f9e3e44} /cleanup
```
or similar:
```
 C:\Windows\system32>bcdedit /delete {ba50fdc0-df08-11de-8f8a-f2e85f9e3e44} /f
```


but always with  **{**...**}**


I hope that will help.


Greets


PS: Take a look on this post [http://ubuntuforums.org/showthread.php?t=1342241](http://ubuntuforums.org/showthread.php?t=1342241)

---

### Post by darkod on 2009-12-02
You do NOT remove wubi by deleting the folder. The same like you do not remove windows apps by just deleting them in Program Files.
You need to use Add/Remove programs like removing any windows app. That takes care of the entry in the windows bootloader and maybe other settings in the computer.
You can try that now but since the folder is missing have no idea if it will work.

---

### Post by footloose143 on 2009-12-02
Since you have already deleted ubuntu wubi related files and messed up your boot menu, I assume you can still login to Windiows ... Google for a tool called MBRFix which will make windows as your primary boot and you wont have any boot menus

---

### Post by ubestos on 2009-12-02
@ darkod

yes and no. The wubi deinstallation, as you are saying, will remove the stuff written by wubi, but in any try thaht I gave it in the past, wubi couldn't remove the Bootloader edit!!!

@ footloose143

wrong. You can not claim, that he messed up the boot-configuration as he deleted the wubi folder, because in that way you cannot prove that enything would be changed. 
MBRfix were an overkill and the total solution in case that he have not the win7 dvd i.e. cmmand: bootrec /fixmbr

@ bayoubadboy

I wish you good luck in any case.

greets

---

### Post by darkod on 2009-12-02
> **ubestos said:**
> @ darkod

yes and no. The wubi deinstallation, as you are saying, will remove the stuff written by wubi, but in any try thaht I gave it in the past, wubi couldn't remove the Bootloader edit!!!



I only used wubi once and briefly before installing ubuntu side-by-side, and it worked for me (removing the entry from windows bootloader when removing wubi). So I'm 100% on my end. :)

Actually footloose gave you excellent idea. Boot with the win7 dvd and select Repair This Computer (after the language selection screen) and that will detect your win7 install and repair your MBR for win7.

---

