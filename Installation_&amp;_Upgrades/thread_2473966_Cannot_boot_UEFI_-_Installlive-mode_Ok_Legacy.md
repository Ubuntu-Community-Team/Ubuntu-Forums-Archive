---
title: "Cannot boot UEFI - Install/live-mode Ok Legacy"
date: 2022-04-19
forum: Installation &amp; Upgrades
---

### Post by ya-simply-better on 2022-04-19
Here's the paste
[https://paste.ubuntu.com/p/82TjdtRqpM/](https://paste.ubuntu.com/p/82TjdtRqpM/)


[LIST]
[*]Issue is black screen on **UEFI **when trying to install or Live-mode from USB (Ubuntu 21.10). 
[*]So I switched to **Legacy **and it(ubuntu) installed. 
[*]But then **Legacy **cannot see from Nvme drive (to boot). 
[*]When trying to boot with **UEFI **it sees nvme but it black screens again (loading ubuntu). 
[/LIST]

I am trying to use boot-repair to convert **Legacy **_into _**UEFI **([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) but boot-repair says, "the current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in you UEFI firmware,....". But when I try to **run boot-repair in live-USB mode** after creating a bootable boot-repair usb it **back screens when on UEFI again**. 

Been trying for days to fix this issue. Any help is truly appreciated!

---

### Post by oldfred on 2022-04-19
What brand/model system?
What video card/chip? Nevermind: from report > GM200 [GeForce GTX 980 Ti]

Have you updated UEFI & SSD firmware?
I downloaded ISO to get latest.
How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows.
You can see your firmware version - FW Rev:
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

Note in a couple of days 22.04 will be released with latest kernel & drivers. And it has long term support.

---

### Post by ya-simply-better on 2022-04-19
> **oldfred said:**
> What brand/model system?
What video card/chip? Nevermind: from report 

Have you updated UEFI & SSD firmware?
I downloaded ISO to get latest.
How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows.
You can see your firmware version - FW Rev:
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

Note in a couple of days 22.04 will be released with latest kernel & drivers. And it has long term support.

FW Rev doesn't have a value it is blank

Trying to follow [https://wiki.archlinux.org/title/Solid_state_drive#Update_under_Linux](https://wiki.archlinux.org/title/Solid_state_drive#Update_under_Linux) using live-mode via usb. initrd from file provided by firmware iso from samsung does not include a root/fumagician directory, it only seems to have a initrd file in it (opening with archievemanager)


Also I tired to make a bootable usb of samsung firmware, it hangs on booting linux kernel on **Legacy**, more black screen on **UEFI**

---

### Post by oldfred on 2022-04-19
I had no issue booting my Samsung ISO. 
I boot in UEFI mode and use grub2's loopmount to boot ISO directly. Was a bit surprised that it worked that way as not all ISO are able to be loopmounted.

I also find revision here:
```
fred@z170-focal-k:~$ udisksctl status
MODEL                     REVISION  SERIAL               DEVICE
--------------------
Samsung SSD 970 EVO Plus 500GB 2B2QEXM7  S4P2NF0M514514L      nvme0n1 


```

---

### Post by ya-simply-better on 2022-04-20
> **oldfred said:**
> I had no issue booting my Samsung ISO. 
I boot in UEFI mode and use grub2's loopmount to boot ISO directly. Was a bit surprised that it worked that way as not all ISO are able to be loopmounted.

I also find revision here:
```
fred@z170-focal-k:~$ udisksctl status
MODEL                     REVISION  SERIAL               DEVICE
--------------------
Samsung SSD 970 EVO Plus 500GB 2B2QEXM7  S4P2NF0M514514L      nvme0n1 


```

Nothing boots for me in UEFI. Black screen on samsung firmware as well.  
Not sure what to do with samsung firmware now, as legacy hangs on kernel boot.


I am not sure if it is a nvme issue as I swapped to a crucial p5 plus 2280, and I am experiencing same issues. 

In addition, the issue of **black screen** when trying to install or live mode from usb when on uefi doesn't have anything to do with nvme firmware.

Can we chat on discord? It's been days of working though this would really appreciate the guidance.

---

### Post by oldfred on 2022-04-20
Many seem to have unrelated issues resolved with firmware updates, so we always want latest firmware & current version of Ubuntu.
Did you ever say what system.

Are you booting with Safe boot mode on Ubuntu boot choices?
With Samsung you may need nomodeset, for nVidia.

And choose to install proprietary drivers, so you get nVidia driver installed.

Before Safe Boot & Ubuntu offering to install correct nVidia driver we had to use nomodeset boot parameter both for live installer & first boot. Then manually install nVidia driver from Ubuntu repository.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ya-simply-better on 2022-04-20
> **oldfred said:**
> Many seem to have unrelated issues resolved with firmware updates, so we always want latest firmware & current version of Ubuntu.
Did you ever say what system.

Are you booting with Safe boot mode on Ubuntu boot choices?
With Samsung you may need nomodeset, for nVidia.

And choose to install proprietary drivers, so you get nVidia driver installed.

Before Safe Boot & Ubuntu offering to install correct nVidia driver we had to use nomodeset boot parameter both for live installer & first boot. Then manually install nVidia driver from Ubuntu repository.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Not sure what you mean by system, the mobo is H12Dsi-N6 supermicro. 

I'll try everything you just mentioned and will report back.

---

### Post by ya-simply-better on 2022-04-20
Added nomodeset and removed quite splash. 

Still see experiencing a blank screen in uefi.

---

### Post by oldfred on 2022-04-20
Perhaps similar & mentions required BIOS/UEFI update.
[https://www.phoronix.com/scan.php?page=article&item=supermicro-h12ssl-i&num=1](https://www.phoronix.com/scan.php?page=article&item=supermicro-h12ssl-i&num=1)

---

### Post by ya-simply-better on 2022-04-21
I got it to install and boot in legacy now. By changing a BIOS setting for NVME & M.2 to AMI Native Support. 

Now I have a raid card issue... If you know any tips with raid card specifically ASUS Hyper M.2. Please send help.

Also, is there anything I need to know about Legacy mode Ubuntu Vs EFI?

---

### Post by ActionParsnip on 2022-04-21
Are you wanting to make a dual boot or will Ubuntu be the only OS on the system?

---

### Post by oldfred on 2022-04-21
Know nothing about RAID.
Other posts often suggest Linux software RAID over "fake" RAID that UEFI/BIOS does. If you want to use drives on another system, the mdadm is easier moved, where any hardware based RAID cannot be easily moved to a new system.

I still suggest gpt partitioning if Linux only on a drive.
Windows requires gpt with UEFI. 

And Ubuntu can boot from a gpt drive with BIOS if you have a tiny 1 or 2MB unformatted partition with bios_grub flag. Or the ESP - efi system partition as FAT32. When first thinking about a new UEFI system, I used gpt with bios_grub partition also had an ESP. Only difference with UEFI & BIOS with Ubuntu is the version of grub. You use grub-pc for BIOS and grub-efi-amd64 for UEFI, but also need correct partitions for grub to install into.

---

