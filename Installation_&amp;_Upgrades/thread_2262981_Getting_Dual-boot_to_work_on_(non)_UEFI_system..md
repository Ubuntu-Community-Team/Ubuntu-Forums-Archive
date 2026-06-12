---
title: "Getting Dual-boot to work on (non?) UEFI system."
date: 2015-01-28
forum: Installation &amp; Upgrades
---

### Post by arnold_layne2 on 2015-01-28
This is the first time I'm working on a Laptop with UEFI so bear with me. I'm gonna bullet-point this to make it quick:

 - HP Envy 6
 - Windows 7 Preinstalled
 - Default BIOS setting: Legacy Support - enabled, Secure Boot - Disabled.


I'm guessing this means Windows 7 has been installed in Legacy mode i.e. without UFI.


So dual booting should be straightforward like the old days right?


I install Ubuntu using the following method:


 - Deleted HP_TOOLS (waste partition)(Due to 4 primary partition limitation)
 - Shrunk Windows partition by 50gb
 - Created 10GB Swap and 40GB ext4 '/' partition for Ubuntu


The installation finishes unsuccessfully with:


    Cannot install grub on /dev/sda: fatal error during installation


Now if I boot my computer, I straight away get a Windows screen asking for the installation CD to do startup repairs (no sign of grub). So the end result is I have neither Windows nor Ubuntu working.


Can someone wiser help me out here? What could be going wrong?

---

### Post by fantab on 2015-01-28
[QUOTE=arnold_layne2]Cannot install grub on /dev/sda: fatal error during installation
[/QUOTE]

There could be two possible reasons:
1... Check the integrity of the downloaded ubuntu.iso with [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM"). If the check fails then you will have redownload the .iso. Try re-burning the .iso to the DVD/USB.
2... There could some corruption on your HDD. The output of the following should give us a hint:

```
sudo parted -l
sudo fdisk -l
```

---

