---
title: "Installation 18.04 Server Fails on SSD NVME SSDPEKKF512G8 disks"
date: 2019-11-24
forum: Installation &amp; Upgrades
---

### Post by DantePasquale on 2019-11-24
Trying to get 18.04 installed on new ASUS motherboard with 2 SSDs. It fails with message: Probe for Installation Device Failed.

I am however able to access both SSDs with parted /dev/nvme0n1 and /dev/nvme1n1 and can create partitions and labels etc.

Help.  This is to replace a failed server and I'm under tight time constraints :(

Installer Log is attached.

---

### Post by oldfred on 2019-11-24
Many NVMe drives need firmware update.
Often system also needs UEFI/BIOS update, even if new.

Is system set for AHCI, not RAID, nor Intel RST in UEFI?

What model Asus?

If Ryzen you may only be able to install 19.10 after UEFI update from vendor that includes the AMD fixes. 
Normally only LTS versions are recommended for servers.

My Asus Z97 Intel based required multiple settings to be changed. And then redone when ever I updated UEFI.
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)

---

### Post by aljames2 on 2019-11-24
Also, probably very basic advice from me, but if you haven&#8217;t, you may want to try the Alternate Server installer.

---

### Post by DantePasquale on 2019-11-24
SOLVED by using the mini.iso network installer alternative -- weird that the other doesn't work tho :(  Thanks for the info and I'll check on the  settings you recommended 'oldfred' :)

---

