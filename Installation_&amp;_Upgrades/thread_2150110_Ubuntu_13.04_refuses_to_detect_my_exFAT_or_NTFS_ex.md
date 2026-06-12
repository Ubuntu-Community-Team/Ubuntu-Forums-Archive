---
title: "Ubuntu 13.04 refuses to detect my exFAT or NTFS external drive!!!"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by Castle_Romeo on 2013-05-31
As above, I've tried using exFAT as well as NTFS for the external hard drive.

I installed exFAT-Fuse as well as NTFS-3G but Ubuntu STILL won't notice the external disk when I turn it on.

I've plugged the external disk into a windows PC and it notices it right away.

Need some help here.

---

### Post by sanderj on 2013-05-31
external ... via USB? If so: Unplug the drive, then plug it in, and post the output of 

```
lsusb
dmesg | tail
```

---

### Post by Castle_Romeo on 2013-05-31
It is actually connected via eSATA to my Ubuntu computer.

---

### Post by Mark Phelps on 2013-06-01
OK, then do a "lspci" to see if the device shows up in the list.  I suspect there may be no ESATA drivers, in which case, your PC will be unable to see the drive.  I tried using an ESATA drive on a previous motherboard running Ubuntu, and it never saw the drive.

---

### Post by sudodus on 2013-06-01
My experience is that eSATA can even be plugged into a standard SATA port via a simple eSATA - SATA cable. You should need no special driver. Maybe there is some problem with the external box or with hot-swapping, that a special eSATA driver would fix.

- Can your computer 'see' the eSATA drive at all? What is the output of the "lspci" command?

- Can you describe the external box? (Since it works with Windows, there should be good electric connection.)

- Can you describe the computer, desktop, laptop, specs? And describe the eSATA connection (built-in or via some adapter or card)! 

- Maybe there is an issue with hot-plugging. Keep the external drive connected, Shut down and cold boot.

- Is there a USB alternative? Yes I know, unless it is USB3 all the way, it will be very slow, but it might work and let you transfer files until you solve the problem with eSATA.

---

### Post by Castle_Romeo on 2013-06-01
Strangely, Ubuntu lists the eSATA controller (Silicon Image SIL 3512) but doesn't see the HDD.....I've tried multiple enclosures and different drives....

---

### Post by Castle_Romeo on 2013-06-01
The external enclosure is a Vantec NexStar USB 2.0 / eSATA drive.

---

### Post by Castle_Romeo on 2013-06-02
I did some searching and apparently, there is a serious compatibility issue with SiliconImage 3512 eSATA cards.

I found a PCI USB 3.0 card off of Newegg that'll work.

Thanx for the replies.

---

### Post by sudodus on 2013-06-02
I hope and think you will be happy with the USB 3 card. Anyway, please post the result and the specs of the card, when you have tested it, to share your experiences with the Ubuntu community :-)

---

### Post by cr15t1 on 2013-06-12
Hello,

I have exactlly the same problem with my external hard drive. You can see here the lspci result

xxxxxxxxxx@xxxxxxxxx-HP-Pavilion-g6-Notebook-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce GT 520M] (rev a1)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Can you please help me?

Thanks in advance

---

### Post by sudodus on 2013-06-13
Hi cr15t1,

and welcome to the Ubuntu Forums :-)

Please make a new thread to discuss your particular problems and make a good descriptive title insteaLd of hi-jacking this thread! You can post a reply in this thread with a link to your new thread (or if you don't know how to do it, send a private message to me, and I can help you getting started with the new thread).

Anyway, as a starter in that new thread, refer to your post here, and also post the output of the following commands within code tags (like the following or marking the output text and clicking on the # icon at the top of the editing window).

[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

Commands:

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
 sudo blkid
```
```
 sudo df
```
```
lsb_release -a
```

It helps if you also describe your computer (at least cpu, ram and graphics chip) and the flavour of Ubuntu (Lubuntu, Xubuntu, Ubuntu, Kubuntu ...)

---

