---
title: "uefi installation problem"
date: 2020-12-07
forum: Installation &amp; Upgrades
---

### Post by zanetto on 2020-12-07
I installed ubuntu 20 on a notebook with uefi and win 10
In windows with command bcdedit I modified uefi boot order in this way:

C:\>bcdedit

Windows Boot Manager
--------------------
identificatore          {bootmgr}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\ubuntu\grubx64.efi
description             Windows Boot Manager
locale                  it-IT
inherit                 {globalsettings}
default                 {current}
resumeobject            {cd1543ba-c71b-11e9-8da9-8d8586573e43}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Caricatore di avvio di Windows
-------------------
identificatore          {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 10
locale                  it-IT
inherit                 {bootloadersettings}
recoverysequence        {cd1543bc-c71b-11e9-8da9-8d8586573e43}
displaymessageoverride  Recovery
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {cd1543ba-c71b-11e9-8da9-8d8586573e43}
nx                      OptIn
bootmenupolicy          Standard

When I turn on my pc, win 10 starts, I do not see grub
If I go to bios and set boot to ubuntu, I see grub and then ubuntu
How can I do?

---

### Post by oldfred on 2020-12-07
What brand/model system?

Some like HP, so not let you change boot order with efibootmgr. Grub uses efibootmgr to set boot order to Ubuntu first when it installs.
To see boot order.
sudo efibootmgr -v

If HP make sure you have updated UEFI, as some have posted that is required.
And then you should be able to change boot order in UEFI settings (not the UEFI one time boot menu).

Note that grub only boots working Windows. So Windows fast start up must be off. And Windows turns fast start up back on.
You then may be able to directly boot Windows from UEFI boot menu, but best to have a Windows repair/recovery flash drive.

---

