---
title: "grub install crashed during install 17.04"
date: 2017-11-16
forum: Installation &amp; Upgrades
---

### Post by seekertom on 2017-11-16
I had ubuntu 17.04 installed on separate int hd with win 7 installed on original hd. I select ubuntu at boot up time by changing boot drive, but do nothing to boot into win 7.
Later I upgraded to 17.10, but do not like the changes compared to 17.04, so decided to reinstall 17.04 from my live cd.
I kept eufi, and chose to install 17.04 alongside 17.1, and resized the partitions to 500tb on 17.1 and 1.5tb for 17.04 partition.

Installation of grub failed: 
" The 'grub-efi-amd64-signed package failed to install into /
target/. without the Grub boot loader, the installed system will not boot."

my question is, Now what?

do I need to try to reinstall grub, if so, how? or redo the whole install from live cd, or do nothing and I will still be able to access both installs of ubuntu, or what???
I'd rather not lose my installed programs or data created under 17.1.

Hope you can help!
thanks, st
:confused:

---

### Post by oldfred on 2017-11-16
Is your Window install BIOS/MBR on drive seen as sda?
The Ubuntu installer for grub only installs to ESP - efi system partition on drive seen as sda.
Some disconnect other drives so Ubuntu drive seen as sda and then it installs correctly. If internal drive that is all that is required, but if external drive more work is required as UEFI only boots from /EFI/Boot/bootx64.efi which grub does not create, and needs to be a copy of shimx64.efi.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

You should have good backups which would include a list of all the additional apps you have installed, all your data and any system configuration changes you may have made. Then you can easily re-install and restore system.

---

