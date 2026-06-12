---
title: "Dual Booting Sony Vaio Issues"
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by k_d2 on 2016-03-13
Hello all,

For the past two days I have been trying to dual boot my Sony Vaio (Model: SVS1512DCXB). It came preinstalled with windows 8 and I upgraded to 8.1. Now I am looking at putting UbuntuGNOME 14.04.4 on it so I can stop running it in a virtual machine.

 However, whenever I restart from the LiveCD my system ALWAYS boots stright into windows!!!

I have tried solutions from these links:
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
and
[http://ubuntuforums.org/showthread.php?t=2227580&page=2](http://ubuntuforums.org/showthread.php?t=2227580&page=2)
and even looked through this bug report:
[https://bugs.launchpad.net/ubuntu/+source/efibootmgr/+bug/1314759](https://bugs.launchpad.net/ubuntu/+source/efibootmgr/+bug/1314759)

For whatever reason nothing I do works!

Running boot-repair yields:
[http://paste.ubuntu.com/15381809/](http://paste.ubuntu.com/15381809/)

Not sure if I should go with the rEFInd route or if there is a fix now. Any suggestions???

---

### Post by Bucky Ball on 2016-03-13
refind has nothing to do with this. For Macs.

There is a key to press to get to the boot device menu at boot on most machines. Many times this key is F12. 

Firstly, I suppose you are booting to the BIOS and changing the boot order to the USB? If that is what you're doing and that is not working, try hitting F12 at boot to get to that boot device menu (or whatever key it is on your machine) and choose the USB from there. This worked on my last machine where changing the BIOS boot order didn't for some odd reason.

The other 'burning' question is ... how did you create the live USB media? What software and what OS was it created on?

* Just checked your boot repair output. The odd thing is you seem to have Ubuntu installed already on sda11. And from the bottom of that output:

> If your computer reboots directly into Windows, try to change the boot order in your BIOS.

Exactly what I suggested previously. :)

---

### Post by k_d2 on 2016-03-14
Unfortunately VAIOs don't allow for changing the bootloader order.

The BIOS menu only allows me to change the boot order for an optical drive, HDD, network, or an external device. :(

---

### Post by fantab on 2016-03-14
From your BootInfo:
```
parted -l:

Model: ATA Hitachi HTS72757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
[COLOR=#ff0000]**1      1049kB  274MB   273MB   fat32           EFI system partition          hidden**[/COLOR]
2      274MB   1819MB  1546MB  ntfs            Basic data partition          hidden, diag
[COLOR=#ff0000]**3      1819MB  2092MB  273MB   fat32           EFI system partition          boot**[/COLOR]
4      2092MB  2226MB  134MB                   Microsoft reserved partition  msftres
5      2226MB  539GB   537GB   ntfs            Basic data partition          msftdata
6      539GB   644GB   105GB   ntfs            Basic data partition          msftdata
9      644GB   645GB   400MB   ext2
10      645GB   663GB   18.0GB  linux-swap(v1)
11      663GB   709GB   46.6GB  ext4
7      709GB   710GB   832MB   ntfs                                          hidden, diag
8      710GB   750GB   40.0GB  ntfs            Basic data partition          hidden, diag
```

Only one ESP is needed per HDD or per System. You have two. However only one has 'boot' flag. No real issue but why do you have two EFI Partitions? Did you create one, why?

```
BootOrder: 0001,0003,2001
Boot0000* EFI DVD/CDROM (MATSHITABD-CMB UJ167AM)    ACPI(a0341d0,0)PCI(1f,2)03120a00040000000000CD-ROM(1,76fac,11c0)RC
Boot0001* Windows Boot Manager    HD(3,363800,82000,6ffba630-c6fc-4d57-84bd-1a90b02043f2)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0003* Ubuntu    HD(3,363800,82000,6ffba630-c6fc-4d57-84bd-1a90b02043f2)File(EFIubuntugrubx64.efi)RC
```

Windows is set as your first boot [0001] and Ubuntu boots next [0003]... 
Now if you go back in your UEFI Menu you should be able to find Boot Order preferences or something like that.
Change that to Ubuntu... and you should be able to see the Grub Menu from where you either boot into Ubuntu or Windows...
Contacting Sony Service for directions may also help..

EDIT: If changing boot order is not an option then you can consider [EasyBCD]("https://neosmart.net/EasyBCD/"), and alternative boot loader for Windows which boots linux as well.

---

### Post by k_d2 on 2016-03-14
One of the partitions is just a back up in case I destroyed the other partition when I was moving files around. May have been over kill looking back but oh well lol

I guess I need to contact Sony and see if there is a way to change the boot loader order...

[ATTACH=CONFIG]267811[/ATTACH]
FYI this is the menu I am working with for boot priority. If anyone wants more pics of the InsydeH20 layout I'll snap some more. It is really limited on options though

---

### Post by oldfred on 2016-03-14
Sony violates UEFI spec that says NOT to use description as part of UEFI boot.
And of course the only valid description is "Windows Boot Manager".
But there are work arounds.
Systems still have to boot hard drive or the fallback boot entry at /Boot/bootx64.efi.
So we make shimx64.efi be bootx64.efi and boot hard drive entry to get to grub.

Boot-Repair copies shim to bootx64.efi, but may not add entry in UEFI. If you have run updates in Boot-Repair try booting hard drive entry.

Details on manually copying files in link in my signature and many other links, of few:
       External drive copy shim to bootx64.efi
[http://askubuntu.com/questions/740290/installed-ubuntu-15-1-on-usb-full-install-but-it-wont-boot](http://askubuntu.com/questions/740290/installed-ubuntu-15-1-on-usb-full-install-but-it-wont-boot)
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
Rename bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair

[/URL]
 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589) 



[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by k_d2 on 2016-03-15
I thought Sony violating terms might be the case. 

I contacted their customer support earlier today and was told that they do not offer support for dual booting a system... Go figure.............

---

