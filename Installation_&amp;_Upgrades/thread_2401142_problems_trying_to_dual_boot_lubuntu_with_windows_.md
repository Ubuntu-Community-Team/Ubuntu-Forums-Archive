---
title: "problems trying to dual boot lubuntu with windows 7"
date: 2018-09-14
forum: Installation &amp; Upgrades
---

### Post by koneko22 on 2018-09-14
i want to start the odin project and they recommend that you either

[LIST]
[*]have dedicated linux machine
[*]have a mac
[*]have dual boot if you want to keep windows
[/LIST]
and they recommend lubuntu, xubuntu or ubuntu and i've choosed lubuntu and set aside 20gb since is just to code and learn everything they teach you i've made a live usb with unetbootin and all fine and dandy until now, it boots perfectly and i use gparted to make my partitions i go with 10 gb for root 2 gb for swap and the rest (8gb) for home and this is where my problems began

i have 3 main problems

[LIST=1]
[*]at boot (try lubuntu) it display something like ''problem loading uefi db x.509 certificate (-22)'' three separate times (i've read that it's maybe due secure boot but it's disabled already)
[*]when i get to choose the instalation type (where it's supposed to appear the ''install lubuntu alongside windows 7'') said option isn't there (dont know if it's really a problem because i use the ''something else'' option)
[*]after i assign the mount points (/, swap, /home) and pick bootloader folder (/dev/sda) and click install now and when it's almost finnished an error pops out that goes like this '' The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot'' and it thows me back to the desktop
[*]bonus problem: the partition that has my windows loader in it (/dev/sda1) that it's supposed to read ''windows 7 loader'' instead appears as ''unknown'' as well the partition that has my windows on it (/dev/sda2) i've been googling almost all day to no avail I have
[LIST]
[*]safe boot dissabled and in standard mode
[*]csm enabled
[*]fast boot disabled (although i dont think that is the same w8 fast boot)
[*]uefi enabled
[*]legacy mode enabled
[*]boot priority uefi first
[*]have lubuntu 64 bits
[/LIST][/LIST]
im at a total lost here and i dont know what else to do if anyone can throw me a line here i would be deeply thankful for and good job withstanding my wall of text! a winner is you!

---

### Post by DuckHook on 2018-09-14
Please do not use odd fonts and formatting. This makes your post difficult to read.

---

### Post by oldfred on 2018-09-14
New UEFI systems have two boot modes. The now 35 year old BIOS/Legacy/CSM mode & UEFI boot mode. 
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

If you have Windows 7 installed it probably is BIOS/MBR configuration. The install DVD is BIOS only, but can be copied to a flash drive and some files moved around to make it UEFI bootable. 
And how you boot install media UEFI or BIOS is then how it installs for both Windows & Ubuntu.

The error you are getting is from trying to install Ubuntu in UEFI boot mode and first drive (not necessarily install drive), does not have an ESP - efi system partition. UEFI recommended gpt partitioning, Windows only boots from gpt with UEFI.
Both Windows & Ubuntu use the same ESP for boot files when dual booting.

You should be able to install Ubuntu in BIOS boot mode, and must specify to install grub2's boot loader to the MBR of drive or sda. 
The other alternative is to backup data & reinstall Windows in UEFI boot mode.

Post this from live installer:
sudo parted -l

---

