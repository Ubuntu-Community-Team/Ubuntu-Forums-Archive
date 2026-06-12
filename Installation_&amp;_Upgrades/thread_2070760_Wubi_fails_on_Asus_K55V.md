---
title: "Wubi fails on Asus K55V"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by afeder on 2012-10-13
Hi. I've been trying to install Ubuntu via Wubi on my new Asus K55V laptop. The installation appears to complete fine without errors, but when I then reboot I get this boot screen error:

[IMG]http://i.imgur.com/tOedcl.jpg[/IMG]

The arcane language here is Danish. The "status" code is "0xc0000098". The final line reads something to the effect of: "Info: The selected entry could not be loaded because the application is missing or corrupt."

The file C:\ubuntu\winboot\wubildr.mbr does exist and is 8 KB. There is also a C:\wubildr of 133 KB and a C:\wubildr.mbr of 8 KB.

Can anyone tell me what might be wrong? Thanks.

---

### Post by Frogs Hair on 2012-10-13
I think that problem is addressed near the beginning of this thread. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by afeder on 2012-10-14
> **Frogs Hair said:**
> I think that problem is addressed near the beginning of this thread. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
I tried replacing C:\wubildr with C:\ubuntu\winboot\wubildr as suggested, but no luck :(

---

### Post by Frogs Hair on 2012-10-14
I would suggest posting on the mega thread with a description of what you have done so far.

---

### Post by bcbc on 2012-10-14
I don't think Wubi works with UEFI: [https://bugs.launchpad.net/wubi/+bug/694242/](https://bugs.launchpad.net/wubi/+bug/694242/)

I don't know much more about this, but that's what Colin Watson (main developer involved with Wubi) indicates.

Edit: grub4dos checks the drive MBR partition table to identify the partitions, so if there is no drive MBR then it won't work. So that could be the issue with UEFI with a GPT partition table.

---

### Post by bcbc on 2012-10-15
afeder, please can you post some more info... run a command prompt (cmd.exe) as an administrator and enter diskpart, list disk as shown below... (I just want to see if it's a GPT disk):
```
Microsoft Windows [Version 6.2.8400]
(c) 2012 Microsoft Corporation. All rights reserved.

C:\Windows\system32>diskpart

Microsoft DiskPart version 6.2.8400

Copyright (C) 1999-2012 Microsoft Corporation.
On computer: XPS

DISKPART> list disk

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          698 GB    30 GB

DISKPART> exit

Leaving DiskPart...

C:\Windows\system32>
```

If it's GPT you might prefer to make a partition and install direct (not with Wubi) to the partition. Wubi is intended to install without partitioning (and it won't make good use even if you create a separate partition for it as it uses a virtual partition that is a single file). (And it's usually simpler partitioning with GPT since it doesn't have the same limits as MBR partition tables)

While you're in that command prompt, maybe you can output the result of "bcdedit" as well e.g. 
```
C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
integrityservices       Enable
default                 {current}
resumeobject            {1632d04d-ac71-11e1-a566-934e06acdba5}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 8
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {1632d04f-ac71-11e1-a566-934e06acdba5}
integrityservices       Enable
recoveryenabled         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {1632d04d-ac71-11e1-a566-934e06acdba5}
nx                      OptIn
bootmenupolicy          Standard

C:\Windows\system32>
```

Thanks

---

### Post by afeder on 2012-10-15
Thanks for your reply.

Here is what I get with diskpart:

```
Microsoft DiskPart version 6.1.7601
Copyright (C) 1999-2008 Microsoft Corporation.
På computeren: CHALLENGER

DISKPART> list disk

  Disk ###  Status         Str.     Ledig    Dyn  GPT
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          931 GB      0 B        *

DISKPART>
```

When trying to run bcdedit I get an error of this type:
```
The boot configuration data store could not be opened. Access is denied.
```
I am running on an "Administrator" Windows user account.

---

### Post by bcbc on 2012-10-15
Did you run cmd.exe as an administrator? (Even if you are running an admin account, you need to do this to open the BCD store).

Hit Windows key + R, type cmd, look above and right click on CMD.EXE, select "Run as administrator".

---

### Post by afeder on 2012-10-15
Thanks. Here is the result:
```
Microsoft Windows [version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation. Alle rettigheder forbeholdes.

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
id              {bootmgr}
device                  partition=\Device\HarddiskVolume1
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
locale                  da-DK
inherit                 {globalsettings}
extendedinput           Yes
default                 {current}
resumeobject            {611231a6-b4f4-11e1-ac1c-d58f298497b2}
displayorder            {current}
                        {fd961a60-1161-11e2-9ca4-e0b9a5fb2be0}
toolsdisplayorder       {memdiag}
timeout                 10
customactions           0x1000043000001
                        0x5400000f
custom:5400000f         {fd961a5c-1161-11e2-9ca4-e0b9a5fb2be0}

Windows Boot Loader
-------------------
id              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 7
locale                  da-DK
inherit                 {bootloadersettings}
recoverysequence        {fd961a5c-1161-11e2-9ca4-e0b9a5fb2be0}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {611231a6-b4f4-11e1-ac1c-d58f298497b2}
nx                      OptIn

Startsektor i realtilstand
---------------------
id              {fd961a60-1161-11e2-9ca4-e0b9a5fb2be0}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

C:\Windows\system32>
```

---

### Post by bcbc on 2012-10-15
I'll refer you to this... [http://askubuntu.com/a/151783/14916](http://askubuntu.com/a/151783/14916)

The first part states:
> First, your partition table is clearly a GUID Partition Table (GPT). Since Windows will boot from GPT disks only if the computer uses an Extensible Firmware Interface (EFI) rather than the older Basic Input/Output System (BIOS), it's clear that you're booting in EFI mode. This is a critical detail, since traditional BIOS solutions are unlikely to work on an EFI system.

And since your disk is marked as GPT by diskpart, I believe you're in the same boat. So I don't believe Wubi can work at all on this computer. The author of that post, Rod Smith, is involved on these forums as [srs5694]("http://ubuntuforums.org/member.php?u=1032238") and probably is the person you want to talk to about UEFI.

It does raise an interesting point, especially if many new computers are coming out with UEFI boot - and secure boot (all Windows 8 for instance), what role Wubi will play in the future. I encourage you to post to that bug report I linked to earlier and see if there's any new response from the developers.

PS if you also asked the same question on Askubuntu.com, I encourage you to edit that and add the additional information that you've provided here, and maybe tag it as "uefi" as well to see if you get some more responses there. The developers seem to visit askubuntu more often than here (or used to anyway).

---

### Post by afeder on 2012-10-15
Thanks for clearing this up. Is there any other way I can install without writing the ISO to a DVD or USB drive? I'd rather not have to go look for a store selling blank DVDs just for that.

---

### Post by bcbc on 2012-10-15
No. There's no way I am aware of. You could run it in a Virtual Machine - this works fine to try out Ubuntu unless you have something that's graphics intensive.

If you do install Ubuntu from a USB/CD then please review the community maintained discussion on EFI boot requirements. e.g. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That page contains links to active bug reports and recommends the unofficial boot-repair tool (on the remix ISO). Personally, I believe boot-repair is a useful but still maturing product, but it's important to be aware of issues others have faced.

---

