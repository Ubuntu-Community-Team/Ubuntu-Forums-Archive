---
title: "Hard drive does not show up in paritioner when installing ubuntu mate"
date: 2019-10-20
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2019-10-20
I shrank the hard drive in windows 10 and used gparted to partition the drive, I turned off fast startup and hibernation, I am thinking I may have to go into the bios setup to turn hibernation off there was well but I do not remember for sure, is there any other reason the drive would not show up except fast boot and hibernation being on? I know the drive is good and it is partitioned.

The laptop is an hp 15-da0053wm, I want to do this right the first time and make it as easy as possible.

Thanks inadvance for any advice.

---

### Post by jeremy31 on 2019-10-20
Any chance this HP is using RAID mode and not AHCI.  I am not sure if Ubuntu recognizes the BIOS RAID mode

---

### Post by wildmanne39 on 2019-10-20
I am not sure, would I check that in the bios at startup?

---

### Post by jeremy31 on 2019-10-20
Yes, it should be in there somewhere especially if it has a small SSD or Intel Optane

---

### Post by wildmanne39 on 2019-10-20
If it is using raid can I change it in the bios without causing any issues for windows?

---

### Post by jeremy31 on 2019-10-20
Switch off RAID and try Windows, it might need to make some adjustments, make backups of Windows.  That model has Intel Optane.

[https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10](https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10)

---

### Post by oldfred on 2019-10-21
You have to install Windows AHCI drivers before changing to AHCI in UEFI settings. You can change back if needed & Windows will work, but then Ubuntu will not.
Very common on Dell.

Is it separate small SSD called Optane memory? That is where Windows puts the hibernation file & it uses the size of RAM. If 16GB or more, and since you should not use Windows hibernation, you can use the SSD as / and put data or /home on HDD.

Historically HP has not been dual boot friendly. It used description as part of UEFI boot and only valid description was "Windows Boot Manager". Some have reported that UEFI updates solve issues. Others say that is only on commercial versions, not home versions.
Multiple work arounds depending on configuration.

General UEFI install instructions in link in my signature.

---

### Post by jeremy31 on 2019-10-21
On the HP I bought last year in order to boot Ubuntu I had to go into UEFI settings, System Configuration, Boot Order, OS Boot Manager and put ubuntu at the top of the list and press F10 twice or all it would do is boot Win 10.  My laptop has similar specs but without the 16GB of Optane

---

### Post by wildmanne39 on 2019-10-21
I could not find a setting to switch to AHCI mode, it looks like with my HP I have to disable the optane memory then it switches to ACHI but it is disabled, I am going to try to install again in a little while, windows was real fast with optane enabled now it is real slow, after I install I should be able to enable optane to be used for windows since ubuntu does not see it correct? 

Thanks to both of you for your help.

---

### Post by wildmanne39 on 2019-10-22
I disabled the optane memory then I was able to install Ubuntu Mate 19.10 with Windows 10 on a new HP laptop, once installed it booted to windows no sign of the grub screen, from windows I was able to boot Ubuntu from advanced options, after I successfully booted Ubuntu Mate then I booted back to windows went to advanced options booted to the UEFI setup and set Ubuntu to boot first and that gave me the grub screen and I am able to boot into Ubuntu Mate and Windows from grub, then I booted back into windows and used the intel software to enable optane memory after which the grub screen disappeared, I booted back into Windows went to advanced options clicked on Uefi and changed Ubuntu to boot first again, now Ubuntu Mate 19.10 is running very smooth now.

Thanks oldfred and jeremy31.

---

