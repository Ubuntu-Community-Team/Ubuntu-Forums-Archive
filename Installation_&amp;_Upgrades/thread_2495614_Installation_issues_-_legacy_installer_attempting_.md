---
title: "Installation issues - legacy installer attempting to partition my installation USB"
date: 2024-02-24
forum: Installation &amp; Upgrades
---

### Post by bestie2 on 2024-02-24
Hi new friends,

[SIZE=2]This is my first time trying to install linux, please forgive me for not knowing what I'm doing. 

I have a laptop, HP Spectre x360, a few years old, which came with windows pre-installed. My goal is to fully replace the windows installation with Ubuntu 23.10. I am *not* trying to dual-boot.

I had been attempting to follow this tutorial: [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) 

So, 
[LIST=1]
[*]I downloaded the iso and installed BalaenaEtcher.
[*]I created an installation USB.
[*]I booted my laptop from the USB and attempted to install.
[*]From within the new installer I connected to a wi-fi network, I selected the full installation option and opted for third-party graphics/wi-fi software (the laptop has a dedicated GPU so I figured I'd want NVIDIA's drivers -- but let me know if I misunderstood this option).
[*]I chose "erase disk and install ubuntu" and clicked through the next few screens.
[*]Several seconds after getting to the screen where you name your device and pick username/password, the installer crashed.
[/LIST]

I tried the above steps again, several times. It wasn't crashing instantly on that page, and there wasn't anything specific I had to do to make the crash happen. It seemed to me that the installer just crashed after being open for a certain amount of time.

So, I went back to the ubuntu install website and noticed the option to use the legacy installer. 
[LIST=1]
[*]I downloaded the iso with the legacy installer and flashed it onto the same USB stick.
[*]I booted from the USB
[*]The installer launched and I began clicking through it
[*]I attempted to make the same choices (e.g. connecting to the internet, downloading software during the install, using third-party drivers)
[*]Because I had chosen to use third-party drivers, I was informed that a Secure Boot password would need to be set. I chose one.
[LIST=1]
[*]I'll also note that I became aware for the first time of UEFI and that I'd need a UEFI partition for my device to work
[/LIST]

[*]I am not prompted as to whether I want to erase the disk or do a dual-boot installation -- instead I am taken directly to the partition screen.
[*]In the partition screen, there's a warning - it says that sda is my installation medium. And in the table below, it only shows sda partitions. The total storage available matches the size of the USB, and there's no option to partition the actual hard drive.
[/LIST]

So, does anyone know why the new installer is crashing? Does anyone know why the legacy installer is only seeing my USB?

Please help!!
[/SIZE]

---

### Post by oldfred on 2024-02-24
Do you have Optane?
Did you change from RAID/Intel RST to AHCI. Windows needs AHCI drivers installed first if using AHCI.

HP is not particularly friendly to Linux. 
The installer uses efibootmgr to change UEFI boot entry to grub, but HP does not recognize change. Users with HP said they can only change boot order by going into UEFI settings & changing order there.

HP Spectre x360 15t  Optane issue
[https://ubuntuforums.org/showthread.php?t=2474790](https://ubuntuforums.org/showthread.php?t=2474790)
[https://chanon.info/install-ubuntu-22.04-on-hp-envy-x360/](https://chanon.info/install-ubuntu-22.04-on-hp-envy-x360/)

Number of threads on x360. It seems HP used that model for many systems. So not all info may be correct or current.
HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume) & 
[https://askubuntu.com/questions/1345338/common-failed-to-install-grub](https://askubuntu.com/questions/1345338/common-failed-to-install-grub)
HP X360 Update UEFI F20, probably newer now
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086) & 
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

### Post by yancek on 2024-02-25
Which version of windows was installed on the computer?  Did you delete and/or format all the partitions which had contained windows leaving only free or unallocated space on the hard drive?  Do you have only one hard drive?  Do you know what EFI and Legacy/CSM installs mean?  Did you verify the downloaded iso as explained on the Ubuntu download page?  Always a good idea but likely not the problem if you can boot the usb.  Did you leave the default for 'device for bootloader installation'?  Often there will be messages shown on screen which give a hint as to the reason for the problem.  Did you get any warning/error messages?  Crash means what, just froze?

When you boot the computer and access the BIOS, do you see any reference to UEFI?  If the computer is less than 12 years old, it is likely EFI.  If you had windows 8 or newer it is likely to be EFI.  If you boot the Ubuntu installer, use the Try option rather than install and open a terminal after you get to the Desktop and run the command below and post the output here:

```
sudo parted -l
```

---

### Post by bestie2 on 2024-02-25
Thanks for the responses.

I went into the bios/uefi menu by pressing f10 during startup.
I found optane settings and disabled optane.
Then, I ran the legacy installer again. This time, I got the option to erase the disk and do a full install.

I have installed ubuntu successfully! Thank you

---

