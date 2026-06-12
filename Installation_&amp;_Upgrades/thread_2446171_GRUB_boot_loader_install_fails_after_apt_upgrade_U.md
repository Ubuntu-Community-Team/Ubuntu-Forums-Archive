---
title: "GRUB boot loader install fails after apt upgrade Ubuntu 20.04"
date: 2020-06-25
forum: Installation &amp; Upgrades
---

### Post by mmann1123 on 2020-06-25
[COLOR=#242729][FONT=Arial]After running apt upgrade on Ubuntu 20.04 something went wrong! 

Either choice returns an error below. This is a windows dual boot. I have backups and I am using timeshift. I am learning but still pretty new to this.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Hoping someone can help me figure out what to do next. Should I continue without installing grub? Do something else?[/FONT][/COLOR]
[IMG]https://i.stack.imgur.com/tb0sG.png[/IMG]

[IMG]https://i.stack.imgur.com/uym1C.png[/IMG]

[COLOR=#242729][FONT=Arial]Gparted:[/FONT][/COLOR]
[IMG]https://i.stack.imgur.com/9BQUX.png[/IMG]
[COLOR=#242729][FONT=Arial]
nvme0n1p1: entire extended partition[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]nvme0n1p6: mounted at /boot/efi[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]nvme0n1p9: filesystem root[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]nvme0n1p8: /home[/FONT][/COLOR]

Please excuse my cross posting, but just realized how active this group is! [https://askubuntu.com/questions/1253108/grub-boot-loader-install-fails-after-apt-upgrade-ubuntu-20](https://askubuntu.com/questions/1253108/grub-boot-loader-install-fails-after-apt-upgrade-ubuntu-20)

---

### Post by oldfred on 2020-06-25
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What I do not like is to see MBR(msdos) partitions with new UEFI systems. I really do not think Ubuntu should allow that. Windows only installs in UEFI boot mode to gpt partitioned drives.

It also looks like your NVMe drives switched or nvme0n1 became nvme1n1? But if using UUID, that should not matter.

---

### Post by mmann1123 on 2020-06-26
I can't install anything at the moment (eg boot-repair) because the missing grub boot loader has a file lock. "Could not get lock /var/lib/dpkg/lock-frontend." 

I think I need to decide which partition to choose (n1p6? or n1np1?), and then I am assuming I should  continue despite "Writing GRUB to boot device failed" error?

After that I think i should be able to install boot-repair.

Thanks for your help!

---

### Post by CelticWarrior on 2020-06-26
Boot Repaiir is to be used in a live session, never in the running system. And the suggestion above about Boot Repair is to obtain the summary report, NOT to apply (yet) any repair.

---

### Post by mmann1123 on 2020-06-26
Gotcha, however I am currently stuck with the problem of figuring out what to do with the GRUB boot loader error (see purple messages above), should I choose n1p6 and then ignore the error and then boot from disk?

---

### Post by oldfred on 2020-06-26
It should give a choice of a drive like nvme0n1, can you scroll up or down?
You do not install grub to a partition like nvme0n1p6.
With old BIOS it only boots from MBR, with UEFI it only boots from ESP - efi system partition.
But UEFI install of grub will auto find ESP, but you have to have an ESP.

Because you have MBR not the UEFI standard of gpt, it may be trying to install the MBR version of grub2? That can, but should not normally be installed to a partition. But that often leads to errors as MBR is still the way BIOS boot which may then have an old non-working install of grub. 

If using UEFI, you really should be using gpt partitioning.
And only if you must have an old BIOS boot version of Windows on same drive, do you need the now 35 year old MBR(msdos) partitioning. 

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

I have used gpt with my old BIOS system starting in 2010, and only used gpt with my UEFI systems.

---

### Post by mmann1123 on 2020-06-26
Unfortunately nvme0n1 isn't an option, can't scroll up or down.  So not sure what to select, only have those two choices. 

Thanks for the info on MBR/GPT


Thinking this might be helpful

 Device         Boot     Start        End    Sectors   Size Id Type
    /dev/nvme0n1p1           2046 1953523711 1953521666 931.5G  5 Extended
    /dev/nvme0n1p5           2048   31250431   31248384  14.9G 82 Linux swap / Solar
    /dev/nvme0n1p6 *    222244864  248848383   26603520  12.7G ef EFI (FAT-12/16/32)
    /dev/nvme0n1p7      248850432  269154303   20303872   9.7G 83 Linux
    /dev/nvme0n1p8      269156352 1953523711 1684367360 803.2G 83 Linux
    /dev/nvme0n1p9       31252480  222242815  190990336  91.1G 83 Linux

Device             Start        End   Sectors   Size Type
/dev/nvme1n1p1      2048     534527    532480   260M EFI System
/dev/nvme1n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme1n1p3    567296  998166527 997599232 475.7G Microsoft basic data
/dev/nvme1n1p4 998166528 1000214527   2048000  1000M Windows recovery environmen

---

### Post by oldfred on 2020-06-26
Neither of those choices will give you a bootable system, so it does not really matter.

Are you booting in UEFI mode.
Your Windows drive looks like UEFI with gpt partitioning.

You need to first resolve why you cannot boot USB flash drive.
If you left UEFI fast boot on, you may not have time to press any key before it starts to boot as it assumes no system changes & UEFI does not write latest hardware/system configuration back to drive.
You may then be able to "cold" boot or full power down, drain all power by disconnecting power & holding power switch. If laptop you have to also remove laptop battery.

I would either convert to gpt or reinstall & restore from your backups.
But convert to gpt also requires use of live installer & total reinstall of grub.

---

