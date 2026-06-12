---
title: "Any One?"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by Alabama-1 on 2011-03-11
Ok I have been using Ubuntu for about 3 years now..I just recently went to install Ubuntu 9.10 as my primary OS.After I installed it everything worked fine..Until I did a distro upgrade from update manager to 10.4 lts..Everything went perfect until It rebooted.So now the only way I can get online is by using My 9.10 livecd Try Ubuntu.
It wont install ,I have tried Numerous times..Everytime I get to the disk Partition of the installation It tells me no Partitions Found..It wont find any where to install it on my comp.I have tried gparted and everything..I cant install anything because I am on an Ubuntu Tour..It's the only way I can  get online! So I am in Desperate need of something..Any Help will be greatly Appreciated!

[COLOR=Red]When I run Gparted this is what i get![/COLOR]


-Roll Tide

---

### Post by Hedgehog1 on 2011-03-11
> **Alabama-1 said:**
> ..Everytime I get to the disk Partition of the installation It tells me no Partitions Found..It wont find any where to install it on my comp.I have tried gparted and everything..I cant install anything because I am on an Ubuntu Tour..It's the only way I can  get online! So I am in Desperate need of something..

-Roll Tide

[SIZE="4"]You may have posted the single most frighting picture on the internet![/SIZE]

You have lost contact with your hard drive.  This can be cause be:

1) Death of hard drive
2) Cable connection to hard drive finally came all-the-way loose
3) Bios is not recognizing the hard drive; may have to fool with Bios Hard Drive Settings to get it to see the drive again.
***EDIT: 4) Upgrading when using RAID***

Are you on a desktop or Laptop?

Have you upgraded/replaced your Hard Drive recently?

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-11
You are/were using a RAID system, huh?  Just noticed it in the picture.  Should have mentioned that...  I will update my list in the previous post...

Please give the details of the raid system, the mix (if any) of IDE and SATA drives..

***The Hedge***

:KS

---

### Post by Alabama-1 on 2011-03-11
I am on  a desktop..dell dimension..I haven't done anything to this Pile..::)
What Do i need to Fiddle with in the Bios settings?
I have tried everything I can think of.Any way of uninstalling/Reinstalling the HD?


This is what I get from My PC!

root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  248M  108M  141M  44% /
udev                  248M  232K  248M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  248M  216K  248M   1% /dev/shm
tmpfs                 248M   40K  248M   1% /tmp
none                  248M   92K  248M   1% /var/run
none                  248M  4.0K  248M   1% /var/lock
none                  248M     0  248M   0% /lib/init/rw

[COLOR=Red]I get nothing from This![/COLOR]
root@ubuntu:~# sudo fdisk -l
root@ubuntu:~# 

root@ubuntu:~# ls -l /dev/disk/by-uuid
ls: cannot access /dev/disk/by-uuid: No such file or directory



oot@ubuntu:~# lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, fast devsel, latency 0
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: [e4] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ed98 [size=8]
    Capabilities: [d0] Power Management version 1
    Kernel driver in use: i915
    Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
    Flags: fast devsel
    Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 0174
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fea0 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Dell Device 0174
    Flags: medium devsel, IRQ 3
    I/O ports at eda0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ee00 [size=256]
    I/O ports at edc0 [size=64]
    Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
    Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Device 200f
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at df38 [size=8]
    Capabilities: [40] Power Management version 2

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
    Subsystem: Dell Device 0174
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at feaef000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at df40 [size=64]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: e100
    Kernel modules: e100


Is there Any way to completely clean my system and install ubuntu?



Thanks for the reply!

---

### Post by Hedgehog1 on 2011-03-11
> **Alabama-1 said:**
> 
[COLOR=Red]I get nothing from This![/COLOR]
root@ubuntu:~# sudo fdisk -l
root@ubuntu:~# 

Is there Any way to completely clean my system and install ubuntu?


Right now, any OS would not install because the system appears to not have a hard drive at all.

You have to get the drive on line again.

Reboot the PC and get into the BIOS, and look and see of the BIOS can see the drive.  IF it cannot, then open the case and check the power and data connections to the drive.  Press them in.

IF the connection seem OK, is the drive even spinning when powered up?  If not, try using an swapping an unused power connection on the drive and make sure it's not just the power feed to the drive.

Please try these steps and report back.

***The Hardware Loving Hedge***

:KS

---

### Post by Alabama-1 on 2011-03-11
Everything is connected fine .The hard drive it's self is spinning..I have been from top to bottom in the bios settings and the tower too..

I got this error once->[COLOR=Red]isolinux:Disk Error 01 , AX = 0201 , drive80[/COLOR]

I think what happened is my MBR files got deleted some how..Not 100% sure though.
 I don't know what to do.I guess I could download some version of windows and try a complete reinstall..?


--------------------------------------

[SIZE=4][COLOR=Red]/EDIT![/COLOR][/SIZE]
Ok..I removed my Western Digital IDE  60GB hard Drive and replaced it with a 40 GB Maxtor Fireball Hard Drive..Everything is Working Fine..Thanks for The Suggestions and Help!

[URL="http://ubuntuforums.org/www.war-lord.org"]www.war-lord.org
[/URL]

---

### Post by Hedgehog1 on 2011-03-12
Alabama-1,

I am glad you are up and running.  Hardware failures are, sadly, an unavoidable reality.  My workmate's email signature says: ***"There are two kinds of computers, those that have failed, and those that will fail."***

Now you can get to some real Ubunutu(ing) and have some fun!

***The Hedge***

:KS

---

