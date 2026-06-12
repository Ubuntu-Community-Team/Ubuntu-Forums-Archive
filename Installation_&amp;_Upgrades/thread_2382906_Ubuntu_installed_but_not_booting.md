---
title: "Ubuntu installed but not booting"
date: 2018-01-18
forum: Installation &amp; Upgrades
---

### Post by pierreb24 on 2018-01-18
Hello !

I just installed ubuntu alongside Windows 10 (with UEFI) on my new computer (long term Ubuntu user, here, but last install from a time when UEFI was not yet a concern), but I'm not able to boot it: there is an "ubuntu" option in the boot options ...

[IMG]https://zestedesavoir.com/media/galleries/407/e9178d0e-c724-4f3a-8b3a-8e55ea189a24.png[/IMG]

... But when I select it, the screen goes black for like half a second, then this menu goes back. I have tried some stuff:

[LIST]
[*]Yet another install
[*]Chroot the system, then perform "install-grup" and "update-grub"
[*]On Windows, "bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi",  which ends up in a second "Windows boot manager" (as you can see from the picture above), but which have the exact same behavior.
[/LIST]
Does someone have a hint on this ? It is quite frustrating.

Note that while checking on internet, I heard of a "secure boot" option, but it is disabled in my case.

Thanks in advance !

---

### Post by kansasnoob on 2018-01-18
I wonder if Ubuntu is installing in UEFI mode or standard MSDOS mode? It would be best for us to see a boot info summary produced by Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

**Do [COLOR="#FF0000"]not[/COLOR] run the recommended repair!** Just select Create bootinfo summary and post the link here. Reason being that we don't want to make things worse - always best to look before you leap.

---

### Post by pierreb24 on 2018-01-18
A pastebin with all the informations is here : [https://pastebin.com/YH3Niej9](https://pastebin.com/YH3Niej9) . As you can see from this log, I have two HDD, one (sda) wich is a ssd and also contains Window, the other (sdb) being a HDD an designed to contain data (I set up the /home to be in /dev/sb2, if I'm correct). It seems to be UEFI, but maybe I miss something :) 

As you recommend, I didn't run the program any further :)

Also, MBR is mentioned at different point, but that's not what we want, isn't it ?

---

### Post by pierreb24 on 2018-01-19
Hep, I have some update. 

First of all, I was able to finally access my installed system by using the [rEFInd boot manager]("http://www.rodsbooks.com/refind/").But we are not exactly done.

First of all, when looking at the output of [COLOR=#0000ff]efibootmgr -v[/COLOR], the line for ubuntu is
[INDENT][COLOR=#0000ff]Boot0001* ubuntu    HD(1,GPT,35fa7791-faf6-4fa8-b040-6f8a1ff6911e,0x800,0xf9800)/File(\EFI\UBUNTU\SHIMX64.EFI)[/COLOR]
[/INDENT]

Strange, since my system have CSM disabled (it was disabled when I install it, it is still disabled, and running [COLOR=#0000ff]udate-grub[/COLOR] does not change anything). And when looking into the partition, the shimx64.efi file is empty (0 bytes).

But, when I'm using rEFInd, I can try to boot to the grubx64.efi, but it says that it is not recognized (wrong format or something). Luckily enough, rEFInd is abble to boot directly to what I think is the kernel image (but I'm not sure whether I did end up in recovery mode or not).


And final weird thing, when booting, Ubuntu is complaining that my /boot/efi (/dev/sda1, see pastebin above) partition have no space left. So maybe ... There is no space left and some stuff were not written correctly ?

If so, why is this partition already full ? (there is the Windows boot manager, but filling the partition would be a really nasty move from them). And more important, how can I fix that without breaking it ?


EDIT: funny thing:


[IMG]https://zestedesavoir.com/media/galleries/407/7e95e1ec-39cd-401c-9db9-40d7ffb73f9c.png[/IMG]

... du -h tells me that the whole thing is 26 Mio big, while the system processor tells me that the whole 512 Mio are used. Wut ?

---

### Post by oldfred on 2018-01-19
Do not run Boot-Repair's autofix. It seems to want to install the BIOS boot version of grub.

It does say ESP is full.
 /dev/sda1      vfat      495M  495M     0 100% /mnt/boot-sav/sda1 
Did you run Summary report from your install?

Default mount of ESP is 0077 (see fstab).
# /boot/efi was on /dev/sda1 during installation
UUID=6ECC-F2A4  /boot/efi       vfat    umask=0077      0       1 

Older installs used defaults, Boot-Repair does change mount to defaults, so it can run updates easily. But they may have changed to 0077, for security reasons.
FAT32 does not support Linux type ownership & permissions, so only the settings mounting in fstab control it. And then perhaps a virus could access it. I still change to defaults so I can update/copy/backup my ESP, but may change on only do those tasks from a live installer.

You need to then use live installer to see what is in ESP. You should have /EFI/ubuntu & /EFI/Boot & /EFI/Microsoft. But none of those should be large. Boot-Repair  report will not show other folders, so cannot tell if others are there also. Boot-Repair also may write its summary info into the FAT32 folder if it can.
Otherwise you may need dosfsck from Linux or chkdsk from Windows on sda1. (Windows does not mount ESP normally, you have to manually mount to run chkdsk).
      
 Must be unmounted, so use live installer and make sure not mounted (like if you click on it to see what is in it.)
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

What brand/model system? Some require work arounds and rEFInd is one of the work arounds for those systems.
Other work arounds are in link in my signature below.

---

### Post by pierreb24 on 2018-01-19
Sorry, I did [COLOR=#0000ff]du[/COLOR] on the [COLOR=#0000ff]/boot/efi/EFI [/COLOR]folder, instead of [COLOR=#0000ff]/boot/efi[/COLOR]. When I do, I get this output:

> 
156K    /boot/efi/EFI/Microsoft/Boot/bg-BG
204K    /boot/efi/EFI/Microsoft/Boot/cs-CZ
204K    /boot/efi/EFI/Microsoft/Boot/da-DK
212K    /boot/efi/EFI/Microsoft/Boot/de-DE
212K    /boot/efi/EFI/Microsoft/Boot/el-GR
156K    /boot/efi/EFI/Microsoft/Boot/en-GB
200K    /boot/efi/EFI/Microsoft/Boot/en-US
204K    /boot/efi/EFI/Microsoft/Boot/es-ES
156K    /boot/efi/EFI/Microsoft/Boot/es-MX
156K    /boot/efi/EFI/Microsoft/Boot/et-EE
204K    /boot/efi/EFI/Microsoft/Boot/fi-FI
13M    /boot/efi/EFI/Microsoft/Boot/Fonts
164K    /boot/efi/EFI/Microsoft/Boot/fr-CA
212K    /boot/efi/EFI/Microsoft/Boot/fr-FR
156K    /boot/efi/EFI/Microsoft/Boot/hr-HR
212K    /boot/efi/EFI/Microsoft/Boot/hu-HU
204K    /boot/efi/EFI/Microsoft/Boot/it-IT
184K    /boot/efi/EFI/Microsoft/Boot/ja-JP
184K    /boot/efi/EFI/Microsoft/Boot/ko-KR
156K    /boot/efi/EFI/Microsoft/Boot/lt-LT
156K    /boot/efi/EFI/Microsoft/Boot/lv-LV
204K    /boot/efi/EFI/Microsoft/Boot/nb-NO
204K    /boot/efi/EFI/Microsoft/Boot/nl-NL
204K    /boot/efi/EFI/Microsoft/Boot/pl-PL
204K    /boot/efi/EFI/Microsoft/Boot/pt-BR
204K    /boot/efi/EFI/Microsoft/Boot/pt-PT
60K    /boot/efi/EFI/Microsoft/Boot/qps-ploc
16K    /boot/efi/EFI/Microsoft/Boot/Resources/en-US
20K    /boot/efi/EFI/Microsoft/Boot/Resources/fr-FR
132K    /boot/efi/EFI/Microsoft/Boot/Resources
156K    /boot/efi/EFI/Microsoft/Boot/ro-RO
200K    /boot/efi/EFI/Microsoft/Boot/ru-RU
156K    /boot/efi/EFI/Microsoft/Boot/sk-SK
156K    /boot/efi/EFI/Microsoft/Boot/sl-SI
156K    /boot/efi/EFI/Microsoft/Boot/sr-Latn-RS
200K    /boot/efi/EFI/Microsoft/Boot/sv-SE
204K    /boot/efi/EFI/Microsoft/Boot/tr-TR
156K    /boot/efi/EFI/Microsoft/Boot/uk-UA
176K    /boot/efi/EFI/Microsoft/Boot/zh-CN
176K    /boot/efi/EFI/Microsoft/Boot/zh-TW
25M    /boot/efi/EFI/Microsoft/Boot
44K    /boot/efi/EFI/Microsoft/Recovery
25M    /boot/efi/EFI/Microsoft
1,1M    /boot/efi/EFI/Boot
4,0K    /boot/efi/EFI/ubuntu/fw
244K    /boot/efi/EFI/ubuntu
26M    /boot/efi/EFI
24K    /boot/efi/.disk
2,5M    /boot/efi/boot/grub/x86_64-efi
4,8M    /boot/efi/boot/grub
4,8M    /boot/efi/boot
465M    /boot/efi/casper
495M    /boot/efi

Could someone confirm me that this 465 Mio [COLOR=#0000ff]casper[/COLOR] file should not be there ? If so, can I remove it ?

@oldfred: Thanks for the reply. Maybe I need rEFInd anyway, but first I would like to understand what happen here and try to fix it without it first. So that you know, I have an AsRock A320M Pro4 motherboard.

---

### Post by oldfred on 2018-01-19
Were you trying to configure a multi-boot system?

casper is part of path to boot files inside the live installer of some versions. I boot ISO with grub2's loopmount and have that in path:
Part of my grub boot of Ubuntu ISO:
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile

Do you have ISOs or extracted ISO in that folder?

---

### Post by pierreb24 on 2018-01-19
I have no idea how this file ends up there (because no, I didn't try to extract an iso there). So you basically confirm me that this file should not be there and can be deleted ?

---

### Post by oldfred on 2018-01-19
It is not a standard UEFI boot file.

If concerned and always good practice if not sure, make a backup. Your entire ESP is not huge, so you should be able to copy to another drive/partition.
I do back up my ESP to other drives.

---

### Post by pierreb24 on 2018-01-20
Ok, yeah, that was it. So I backup the entire efi directory, then I get rid of the casper directory, grub-install and upgrade-grub and that's it ! Thanks everyone :)

(This is an odd problem, though, maybe I should send a ticket to grub mainteners to notify them that no warning appears if the partition is full)

---

### Post by oldfred on 2018-01-20
Glad it is working.

I do not think anywhere they tell you system is full. It probably is considered a user requirement to maintain his system. And yours is the first I have seen with full ESP. And many systems only have the default Windows 100MB size for the ESP.

We have had lots of issues where /boot with LVM installs was not particularly large and then they started downloading lots of kernels filling it and making it difficult to houseclean. It has taken a long time, but now /boot is a bit larger and they automatically keep only two kernels.

---

