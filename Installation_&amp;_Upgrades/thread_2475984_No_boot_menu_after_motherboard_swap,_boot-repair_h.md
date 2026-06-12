---
title: "No boot menu after motherboard swap, boot-repair hangs when run"
date: 2022-06-13
forum: Installation &amp; Upgrades
---

### Post by saja4007 on 2022-06-13
I had the motherboard swapped out on my Lenovo X1 Carbon laptop.  Previously I had resized the original Windows 10 install and added 20.04 along side it.  I think it was doing a UEFI boot and I had secured boot disabled.  After the swap the computer boots directly into windows.  I booted a Live thumb drive and installed boot-repair.  The output of the diagnostic is here: [https://pastebin.ubuntu.com/p/bwnFVg6v6C/](https://pastebin.ubuntu.com/p/bwnFVg6v6C/)

I then tried to run the recommended repair, but the menu was stuck sitting at "Applying Changes. This may take several minutes." for at least half an hour.  I then realized I had run it without sudo and thought maybe that was the problem, so I killed the process and ran the repair again with sudo, but the same thing happened, just sitting at "Applying Changes."

Any suggestions?

---

### Post by oldfred on 2022-06-13
When you install grub, it uses efibootmgr to create an UEFI boot entry & add the /EFI/ubuntu folder into the ESP.
You could just use efibootmgr to recreate your Ubuntu boot entry in new motherboard's UEFI, but since you have Boot-Repair, use its advanced mode and choose the total reinstall of grub. 

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by saja4007 on 2022-06-13
Will the Advanced Mode operate differently from the auto mode I chose before?  I checked /var/log/boot-repair and it looked like there was an error:
...
[email]SET@_progressbar1.pulse[/email]()
[email]SET@_progressbar1.pulse[/email]()

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p5,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


/usr/share/boot-sav/gui-actions.sh: line 234: ${LISTOFPARTITIONS[$PARTTOUNFLAG}: bad substitution
[email]SET@_progressbar1.pulse[/email]()
[email]SET@_progressbar1.pulse[/email]()
[email]SET@_progressbar1.pulse[/email]()
...

---

### Post by oldfred on 2022-06-14
It looks like default repair would be the same.
Did you run it?

You then should get a new UEFI entry and it would be the new default:
sudo efibootmgr -v

---

### Post by saja4007 on 2022-06-14
Right, when I run boot-repair through the Advanced Options menu it looks like it gets stuck at the same point as the default repair, so something in the procedure doesn't seem compatible with my system and it doesn't end up making any changes to the uefi configuration.

sudo efibootmgr -v
> BootCurrent: 001D
Timeout: 0 seconds
BootOrder: 001C,001D,0000,001A,001B,001E,001F,0020,0021,0022
Boot0000* Windows Boot Manager    HD(1,GPT,80c78a53-97d8-4880-8311-b2695b9f1180,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0010  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Asset Information    FvFile(da465b87-a26f-4c12-b78a-0361428fa026)
Boot0015  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
Boot0016  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
Boot0017  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0018  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0019  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot001A* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot001B* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot001C* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001D* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot001E* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot001F* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri([https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi](https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi))
Boot0020* ON-PREMISE    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri()
Boot0021  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35400)
Boot0022  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0023* IDER BOOT CDROM    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
Boot0024* IDER BOOT Floppy    PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
Boot0025* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0026* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)


Is there another documented procedure I can run using efibootmgr or another tool to restore the previous configuration?

---

### Post by saja4007 on 2022-06-14
Alright, found another post by you last year suggesting:

> sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP. 				

so in my case that would be:

sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/nvm0n1p1 -p 1

I'm not sure what the difference between shimx64.efi and grubx64.efi is, other examples of the efibootmgr command are pointing to grubx64.efi.  Also I would assume the path is case-sensitive?  I have .efi rather than .EFI as in the above example.

---

### Post by oldfred on 2022-06-14
Run this before & after to confirm that Ubuntu entry gets added. Or post error messages.
sudo efibootmgr -v 
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1
sudo efibootmgr -v 

Assumes you want ubuntu as name, that /EFI/ubuntu folder with shimx64.efi exists and is in partition 1 (-p 1) of drive nvme0n1.
For more details on efibootmgr & settings/parameters
man efibootmgr

---

### Post by saja4007 on 2022-06-14
Thanks for your help! I now have grub back and can boot into ubuntu again.  Do you think it would be worth it to file a bug with boot-repair?

---

### Post by oldfred on 2022-06-14
Boot-Repair is primarily running standard Linux tools.
It looks like error was related to one of your partitions. It trys to open all partitions to check for installs.
Do you have some partition or does Lenovo have one that is somehow restricted?

If not I might file a bug, but you need to include list of all partitions with details.
What does this show?
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid

---

### Post by saja4007 on 2022-06-14
I wonder if it was partition 2, some small 16Mb Microsoft thing, looking  at the pastebin dump from boot-repair it doesn't look like it was able  to get info on that partition.

> lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid 
NAME FSTYPE   SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID
nvme0n1
&#9474;           953.9G                                   
&#9500;&#9472;nvme0n1p1
&#9474;    vfat     260M  36.3M SYSTEM
&#9474;                               EFI system partition
&#9474;                                         /boot/efi  041B-BA25
&#9500;&#9472;nvme0n1p2
&#9474;              16M              Microsoft reserved partition
&#9474;                                                    
&#9500;&#9472;nvme0n1p3
&#9474;    ntfs      90G        Windows
&#9474;                               Basic data partition
&#9474;                                                    BA201EBA201E7E17
&#9500;&#9472;nvme0n1p4
&#9474;    ntfs    1000M        WinRE_DRV
&#9474;                               Basic data partition
&#9474;                                                    725C1F0A5C1EC92D
&#9500;&#9472;nvme0n1p5
&#9474;    ext4    76.5G  25.7G                 /          950416d7-a1b9-4082-b85e-20c378ba78ff
&#9492;&#9472;nvme0n1p6
     ext4   786.1G  15.7G                 /home      1d832096-de1c-4b99-9d59-7f38bcb67288


---

### Post by oldfred on 2022-06-14
The Microsoft Reserved is a required partition.
It has to be unformatted so many tools give an error.

---

