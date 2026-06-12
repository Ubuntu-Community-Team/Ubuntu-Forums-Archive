---
title: "Looks like buggy APIC routine while formatting hard disk partitions"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by harisund on 2005-09-05
Hello everyone 

I am trying to install Hoary 32bit on my new laptop. Here are some specifications to start out with:
Compaq Presario V2000z
AMD Turion(TM) 64 ML-28 (1.6GHz/512KB L2 Cache)
ATI RADEON(R) XPRESS 200M w/productivity ports
60 GB 4200 RPM Hard Drive (Fujitsu MHT2060 AT)

Oh and in case it is needed, I am running a Phoenix BIOS


When trying either of them, everything goes smoothly (including hardware detection and acquiring an IP of 192.168.0.101 from my router's DHCP Client connected through ethernet-LAN) it comes to the disk partition stage.

Here is a map of my 60 GB hard disk (IDE)

hda1 = 10 GB -- Windows XP home, that came with my computer (BOOTABLE)
hda2 = 25 GB -- NTFS formatted partition, with my data
The rest is unused. I then create
hda3 = 10 GB -- ext3, mount point /
hda4 = 14 GB -- ext 3, mount point /home
The remaining is swap

A switch to vt 4 (Alt+F4) reveals the following:

Sep 5 12:54:39 main-menu[326]: DEBUG: Configure harddrive-detection, status:0
Sep 5 12:54:39 main-menu[326]: DEBUG: virtual package harddrive-detection
Sep 5 12:54:39 kernel: Journalled block device driver loaded
Sep 5 12:54:39 kernel: SGI XFS with ACLS, no debug enabled
Sep 5 12:54:39 kernel: SGI XFS Quota Management subsystem
Sep 5 12:54:39 kernel: Adding Swap: 679856k swap-system (priority -1)

And then I ask it to apply changes to the hard disk.. and BOOM ! This is when the problems start to occur

The system becomes extremely slow, and all I see is a blue screen (Hmm.. BSOD, eh Smilie ). The hard disks aren't formatted at all, and the installation stops right there for either of my discs.

A switch to vt4 makes me wait a real long time before the terminal shows me the messages, and here is what I constantly see repeated

SEP 5 12:55:30 kernel: apic error on cpu0: 40(40)

I also tried the boot parameter for "disabling buggy apic routines" and haven't been able to observe any changes.

Could anybody please help me out with this one?

Thank you very much.

Regards

---

### Post by GordSellar on 2006-05-09
[quote=harisund]Hello everyone 

I am trying to install Hoary 32bit on my new laptop. Here are some specifications to start out with:
Compaq Presario V2000z
AMD Turion(TM) 64 ML-28 (1.6GHz/512KB L2 Cache)
ATI RADEON(R) XPRESS 200M w/productivity ports
60 GB 4200 RPM Hard Drive (Fujitsu MHT2060 AT)

Oh and in case it is needed, I am running a Phoenix BIOS


When trying either of them, everything goes smoothly (including hardware detection and acquiring an IP of 192.168.0.101 from my router's DHCP Client connected through ethernet-LAN) it comes to the disk partition stage.

Here is a map of my 60 GB hard disk (IDE)

hda1 = 10 GB -- Windows XP home, that came with my computer (BOOTABLE)
hda2 = 25 GB -- NTFS formatted partition, with my data
The rest is unused. I then create
hda3 = 10 GB -- ext3, mount point /
hda4 = 14 GB -- ext 3, mount point /home
The remaining is swap

A switch to vt 4 (Alt+F4) reveals the following:

Sep 5 12:54:39 main-menu[326]: DEBUG: Configure harddrive-detection, status:0
Sep 5 12:54:39 main-menu[326]: DEBUG: virtual package harddrive-detection
Sep 5 12:54:39 kernel: Journalled block device driver loaded
Sep 5 12:54:39 kernel: SGI XFS with ACLS, no debug enabled
Sep 5 12:54:39 kernel: SGI XFS Quota Management subsystem
Sep 5 12:54:39 kernel: Adding Swap: 679856k swap-system (priority -1)

And then I ask it to apply changes to the hard disk.. and BOOM ! This is when the problems start to occur

The system becomes extremely slow, and all I see is a blue screen (Hmm.. BSOD, eh Smilie ). The hard disks aren't formatted at all, and the installation stops right there for either of my discs.

A switch to vt4 makes me wait a real long time before the terminal shows me the messages, and here is what I constantly see repeated

SEP 5 12:55:30 kernel: apic error on cpu0: 40(40)

I also tried the boot parameter for "disabling buggy apic routines" and haven't been able to observe any changes.

Could anybody please help me out with this one?

Thank you very much.

Regards[/quote]

Did you ever figure it out? I have the same issues on my own Presario and while it seems to to affect performance, it'd be nice to know what the hell is behind it.

---

