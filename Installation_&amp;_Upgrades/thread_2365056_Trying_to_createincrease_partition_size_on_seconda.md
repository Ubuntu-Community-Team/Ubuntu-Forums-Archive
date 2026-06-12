---
title: "Trying to create/increase partition size on secondary disk."
date: 2017-07-01
forum: Installation &amp; Upgrades
---

### Post by joaocrespo on 2017-07-01
Hello world.

I recently purchased a new computer:
[B][B]AMD Ryzen 5 1600 Hexa-Core 3.2GHz c/ Turbo 3.6GHz 16MB SktAM4
[/B][/B]

[B]Motherboard MSI B350M MORTAR ARCTIC

It is also my first computer running UEFI instead of Bios.[/B]

It contains a brand new SDD (dev/nvme0n1) and a not very old 4 TB HDD (dev/sda).

I installed windows 10 on the HDD (using only 2 Therabytes, because i intend to use the rest for media storage), and ubuntu later on the SDD.

When i tried to create a partition (ext4 , ext3 does not matter) on the free space of the HDD i get this error:

[TABLE]
[TR]
[TD="colspan: 2"]**riar Partição primária #1 (ext4, 2.20 TiB) em /dev/sda**  00:00:00    ( ERRO )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] criar uma partição vazia  00:00:00    ( ERRO )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] mensagens da libparted    ( INFO )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *o tamanho da partição de 4718852096 sectores excede o valor máximo imposto para a tabela de partição msdos que é de 4294967295*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

Which translates in english to something like:

 the size of the partition of 4718852096 sectors exceeds the maximum value for the msdos partition table which is 4294967295.

This is weird because in this disk i´m able to create partitions in ext4, and resize the NTFS ones, just i cant seem to be able to do anything that exceeds this arbitrary limit in terms disk partitions size.

I searched the UEFI configurations, but i cant locate any weird config that may be limitating disk usage.

Any suggestions?

Thanks in advance.

---

### Post by oldfred on 2017-07-01
UEFI installs normally and should use gpt partitioning.
And gpt partitioning is requried for any partitioning over 2.2TiB.

But if you install Windows in the 35 year old BIOS/MBR configuration it will only be MBR not gpt and then you have converted your 4TB drive to 2TB.
How you boot install media is then how it installs. So if you boot in BIOS/CSM/Legacy it installs in BIOS mode.

Post this:
sudo parted -l

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

