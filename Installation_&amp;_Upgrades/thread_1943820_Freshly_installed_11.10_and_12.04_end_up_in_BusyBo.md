---
title: "Freshly installed 11.10 and 12.04 end up in BusyBox"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by eekie on 2012-03-20
I recently bought a new motherboard and processor, replacing a MSI 790FX-GD70/ Phenom955 with an Asus sabertooth 990FX/ Bulldozer 8150, all AMD chips, and had to reinstall the linux operation systems Kororaa16x64, Fedora16x64 and Ubuntu11.10x64. Windows was recovered from a system backup. I keep the o.s.'s on two fake raid 0 configs consisting of two ssd's and two hdd's created with the onboard raid controller.
Kororaa and Fedora installed flawlessly, but Ubuntu12.04 beta gave problems during installation of the bootloader. It insisted on putting the bootloader on sda where I specified /dev/mapper/pdc_fgddehjig. Sda happens to be a disk in the raid array, so I was not surprised the system declared it a fatal error.So I decided to not install the ubuntu grub2 bootloader, and to use the grub2 bootloader from Kororaa instead.
Ubuntu12.04 then starts but half way it starts spitting errors and warnings:

gave up waiting for root device
common problems:
-Boot args (cat /proc/cmdline)
-Check root delay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT: /dev/dm-7 does not exist Drop into shell 

BusyBox .....
(initramfs)


DMraid module is present and if I give the command:
dmraid -ay
all raid partitons are being shown and then it says it can go any further because a non existing raid partition is not there.

First I thought it to be a beta bug, but when I installed 11,10 again I got exactly the same problems.
Now I suspect Ubuntu has a problem with the motherboard chipset of the AMD 990FX.
Can anyone provide me with a sound solution?

---

### Post by oldfred on 2012-03-20
Were you installing from a liveCD or the Alternate installer?

 The Desktop liveCD does not have the extra drivers for RAID & LVM as they are more like server installs not typical desktops.

I do not know it this can install to your configuration or not but it is a good way to run the boot info script which documents your system.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by eekie on 2012-03-21
I used the alternate cd for 12.04 and the live cd for 11.10.
When I type the command dmraid -ay in the BusyBox all my raid partitions show up as activated. The boot repair disk does not see any raid partitions. Is this an imcompatibility with the 990FX chip?

---

### Post by oldfred on 2012-03-21
There are some BIOS settings that can cause issues but I know so little about RAID that I do not know.

The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

If running from liveCD or USB add these first:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

---

### Post by eekie on 2012-03-22
I tried the fixes, but no deal. Now I have made the test of installing the distro's on my old computer with msi K9N2 platinum mobo. 11.10 does fine but 12.04 gives the same problem as at the asus sabertooth: it can't install the bootloader at the raid partition. Then after updating grub2 under Kororaa it starts up in text mode and stops in the busybox telling it can't find the bootpartition.
I don't expect a beta to be perfect, but the failure of 11.10 on the FX900 sabertooth has undermined my trust in Ubuntu.

---

### Post by andrew.46 on 2012-03-30
A little aside of your question: It is good to see a fellow Bulldozer 8150 user :). I hope you agree with my assessment that it is an absolutely screamingly fast chip despite all of the gloom and doom reviews?

---

### Post by klqn on 2012-04-20
> **oldfred said:**
> There are some BIOS settings that can cause issues but I know so little about RAID that I do not know.

The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

If running from liveCD or USB add these first:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

Thank you - this fixed it for me.  I don't understand why Ubuntu can't resolve this issue.  Why Centos/Fedora doesn't have this issue.

---

