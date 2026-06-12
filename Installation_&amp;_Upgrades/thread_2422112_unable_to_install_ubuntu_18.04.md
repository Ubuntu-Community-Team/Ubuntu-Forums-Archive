---
title: "unable to install ubuntu 18.04"
date: 2019-07-02
forum: Installation &amp; Upgrades
---

### Post by pagno2 on 2019-07-02
-ASUS VivoBook with Windows 10
- HD 500 GB SSD
- BIOS version doesn't have "launch CSM" therefore when abilitating boot from USB I could only DISABLE "fast boot" and "security boot control"
- fast start up disabled with "powercfg &#8211;h off"
- ISO in USB drive done both with Universal USB and Rufus, andboth FAT 64 and NTFS
- when booting from USB three possibilities pop up: 1. windows; 2. UEFI SANDISK Partition 1; 3. Enter setup
- choose nr. 2, a list of BIOS errors pop up in a black screen but at the end I can choose between "install ubuntu" and "try ubuntu" (still in a black screen)
- either choice stops at step 5 of this guide [https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/](https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/)
that is to say I can't select the "installation type", it says "you need at least 8 GB, this computer has only 4 GB"
- from this information I understand it is trying to install it in the USB and not in the PC HD

Can you help?
GA

---

### Post by CatKiller on 2019-07-02
Windows 10 defaults to never shutting down properly, and turns that option back on with updates if you disable it, and just suspends instead. They call this option "fast startup" This leaves the hard drives in a dirty state and Ubuntu won't even show that they exist: any change to them when they're in that state would completely mess up your Windows install. Turn that option off in Windows and you should have more luck.

---

### Post by pagno2 on 2019-07-02
Thanks
is "fast start up" different from "fast boot"? I did disabled "fast boot" in bios.
If yes, where can I find that?
GA

---

### Post by ajgreeny on 2019-07-02
fast-startup is a setting in Windows I think, not in the BIOS/UEFI settings but I had to search for how to disable it as I do  not use Windows any more so it's not something that bothers me.
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by oldfred on 2019-07-02
Often issues are common across similar models of same brand. Bigger issues between Intel & AMD versions. These may have some hints on unique issues of Asus Vivoboots.

       Asus Vivobook S15
[https://ubuntuforums.org/showthread.php?t=2375408](https://ubuntuforums.org/showthread.php?t=2375408)
ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
[https://ubuntuforums.org/showthread.php?t=2402972](https://ubuntuforums.org/showthread.php?t=2402972) 
            Asus vivoPC M32CD Skylake boot options pci=nomsi i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977&p=13463389#post13463389](http://ubuntuforums.org/showthread.php?t=2312977&p=13463389#post13463389)

---

### Post by CatKiller on 2019-07-02
> **pagno2 said:**
> Thanks
is "fast start up" different from "fast boot"? I did disabled "fast boot" in bios.
If yes, where can I find that?
GA

Yes, it's a different thing.

> Head down to your search bar at the bottom left, and type in ‘Control Panel’ and hit Enter.
Head into the Power Options, and then go into “Choose what the power buttons do” on the left.
Hit “Change settings that are currently unavailable” and then hit “Turn on fast startup” so that the checkmark is no longer there.
Save your changes.

[https://www.techadvisor.co.uk/how-to/windows/how-disable-fast-startup-in-windows-10-3682197/](https://www.techadvisor.co.uk/how-to/windows/how-disable-fast-startup-in-windows-10-3682197/)

---

### Post by yancek on 2019-07-02
Fast Startup info at the link below including how to disable it.

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by pagno2 on 2019-07-03
Thanks
Found it
but disabling "fast startup" hasn't brought any improvement.
Ubuntu tries to install onto the usb drive.
Basically ubuntu, while installing from USB, doesn't see the SSD hard disk.
GA

---

### Post by oldfred on 2019-07-03
Have you updated UEFI.
Are drives set for AHCI? Not RAID nor Intel RST?

---

### Post by mastablasta on 2019-07-05
does the hard disk have unformated free disk space ?

---

### Post by pagno2 on 2019-07-07
> **mastablasta said:**
> does the hard disk have unformated free disk space ?
Wouldn't say so:
1. 0 partition 260MB (partition of system EFI)
2. OS C: 475 GB NTFS
3. Recovery: 850 MB NFTS
all are blue colored and labelled as "primary partition"; the first isn't labelled as NTFS, which should be ok as far as I know


I also typed "powercfg &#8211;hibernate off" in Windows Powershell (admin). No results.

Isn't there a way to TOTALLY GET RID of Windows and then install whatever you want?

---

### Post by mastablasta on 2019-07-08
> **pagno2 said:**
> Wouldn't say so:
1. 0 partition 260MB (partition of system EFI)
2. OS C: 475 GB NTFS
3. Recovery: 850 MB NFTS
all are blue colored and labelled as "primary partition"; the first isn't labelled as NTFS, which should be ok as far as I know


I also typed "powercfg –hibernate off" in Windows Powershell (admin). No results.

unformatted disk space is needed

> 
Isn't there a way to TOTALLY GET RID of Windows and then install whatever you want?
yes, format the drive (you also overwrite all data on the disk). to see the drive it really has to be fully unmounted in windows

---

