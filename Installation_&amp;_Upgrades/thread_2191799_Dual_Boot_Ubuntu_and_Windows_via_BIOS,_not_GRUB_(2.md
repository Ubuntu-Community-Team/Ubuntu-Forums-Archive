---
title: "Dual Boot Ubuntu and Windows via BIOS, not GRUB (2 harddrives)"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by Palu on 2013-12-04
Hello,

I don't want Windows to show up in GRUB because the only reason I'll ever want to use it is if I have a seasonal (winter) hankering for Civ 5. Currently I have Ubuntu on an SSD and a 1TB HD for storage of virtual machines and misc development. I thought about using BIOS to switch the boot order after disconnecting the SSD and booting from a Win 7 install CD / USB / whatever. Then I'd simply keep the BIOs on the SSD until I get my Christmastime Civ 5 cravings. Does anyone forsee problems with that or have recommendations of things I shoudl research? The only think I can think of is that I might need to re-educate myself about partition tables and disk formats so that I know how to format the 1 TB HD for Windows and Civ 5 (with most of it still reserved for development / VMs).

---

### Post by oldfred on 2013-12-04
If you have two drives you can keep grub on the SSD and have Windows on hard drive and keep Windows boot loader in the hard drive's MBR. Then in grub turn off os-prober so it does not add Windows to grub menu.
Then from one time boot key or BIOS you can still boot Windows.

If installing Windows in a two drive system, make sure BIOS is set to boot the drive you install Windows to as first boot drive. Otherwise the hidden 100MB boot partition will be put on the first boot drive in BIOS and just overwrite whatever is there, since it does not see Linux partitions correctly.

       Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

