---
title: "Alternate install 11.04 doesn't boot"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by Skoj on 2011-07-21
Hi,


I just assembled a htpc and wanted to install Ubuntu. The htpc consists of:
- Gigabyte H67MA motherboard
- i3 2100
- Sapphire HD 6450
and two 2 TB HD's in AHCI, RAID 1 (setted up in bios of H67)

During the first installation, I received an error saying the ext4 couldn't be written. After searching on google I found out that I needed the alternate installation image since I'm using the motherboard's raid controller.

I began the second installation using the alternate installation image and it asks me to activate the RAID controller, I confirmed and then I chose "use entire disk" (without LVM). The installation also installed all updates using the network.

Unfortunately after install, nothing happens: Loading Operating System ... and a blinking cursor.

Boot sequence: 1. Hard disk, 2. CD-ROM

I hope you guys can help me out here..

Thanks

Edit: I tried a live cd (XBMC Live, based on Ubuntu 10.04), but after choosing to start up the live environment, it didn't load. So I guess it's a driver problem?
Edit2: I installed windows 7 64 bit without any problems.. So I guess the system is well assembled.

---

### Post by dino99 on 2011-07-21
it should works:

[http://askubuntu.com/questions/22237/when-will-we-get-sandy-bridge-support](http://askubuntu.com/questions/22237/when-will-we-get-sandy-bridge-support)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

note: always the slowest speed for burning

---

### Post by Skoj on 2011-07-21
So I need to create a software RAID, although there is already a RAID drive configured (that I use entirely for the installation) by the RAID controller on the motherboard?

---

### Post by dino99 on 2011-07-21
you have to know which raid chipset is used on MB, then google around ubuntu+thischipset

note: they often are "fakeraid" eg not fully hardware like a card

---

### Post by Skoj on 2011-07-21
It's the [H67 chipset]("http://www.intel.com/products/desktop/chipsets/ec-h67/h67-overview.htm"), but I couldn't find any posts or websites about raid issues with the H67.

---

### Post by dino99 on 2011-07-21
the first thing to do is to closely check how hardware are plugged as explained into MB doc, specially the raid section. And dont forget the bios settings indeed.

---

### Post by Skoj on 2011-07-21
The 2 hard disks are connected to the 2 available SATA6 slots. In the BIOS I have set the PCH SATA Control Mode to RAID(XHD) (in stead of IDE or AHCI) and configured a RAID array by creating a RAID Volume with RAID 1 level. The 2 hard drives were automatically assigned to the array after which I confirmed to create the RAID volume. Following the MB's guide, the last step is to install the SATA RAID/AHCI controller driver during the OS installation. Without the driver the hard drive may not be recognized during the setup process. Unfortunately, there is only a windows driver available on the [Gigabyte website]("http://be.gigabyte.com/products/product-page.aspx?pid=3768&dl=1#driver").

During the alternate installation, ubuntu asked me to activate the RAID driver, which I did and ubuntu seemed to have successfully partitioned the raid volume.. A wrong driver perhaps?

---

