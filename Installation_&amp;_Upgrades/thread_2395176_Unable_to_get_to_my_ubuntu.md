---
title: "Unable to get to my ubuntu"
date: 2018-06-27
forum: Installation &amp; Upgrades
---

### Post by jaimec14 on 2018-06-27
So I had windows 7 with ubuntu 16.04, and I installed windows 10 on the windows 7 partition, and then I lost the grub menu, so I went to liveDVD and run the boot repair, and that showed the grub menu, but in the process I got message saying that the OS is far from the start, and went to this link [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition), I did everything there, and got the same message, and same error, and when trying to access to ubuntu, i got this error kernel panic - not syncing vfs unable to mount root fs on unknown-block(0 0), this is the link i got while trying to do the tutorial from the boot partition [http://paste.ubuntu.com/p/ndmnbTNJDD/](http://paste.ubuntu.com/p/ndmnbTNJDD/) hope someone can help me getting back my ubuntu OS

---

### Post by Xian on 2018-06-28
This discussion of the same error message may be helpful:

[https://ubuntuforums.org/showthread.php?t=1751574](https://ubuntuforums.org/showthread.php?t=1751574)

---

### Post by jaimec14 on 2018-06-28
I tried whats on that thread, didnt work

---

### Post by Dennis N on 2018-06-28
This information may be helpful in recovering Ubuntu:

BIOS system:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Or are you using UEFI?

---

### Post by jaimec14 on 2018-06-28
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *       205200 668564738 668359539 318.7G  7 HPFS/NTFS/exFAT
/dev/sda2       668565504 669569023   1003520   490M 27 Hidden NTFS WinRE
/dev/sda3       669571070 976771071 307200002 146.5G  5 Extended
/dev/sda5       671619072 968577023 296957952 141.6G 83 Linux
/dev/sda6       968579072 976771071   8192000   3.9G 82 Linux swap / Solaris

I tried whats on that link, fdisk -l shows me this, and when I try to do grub install /dev/sda5 i get this error grub-install: error: failed to get canonical path of `/cow'.

---

### Post by jaimec14 on 2018-06-28
Solved everything using this command on windows terminal `[COLOR=#111111][FONT=Consolas]bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi`[/FONT][/COLOR]

---

