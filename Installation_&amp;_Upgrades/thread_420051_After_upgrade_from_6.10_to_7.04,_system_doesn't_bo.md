---
title: "After upgrade from 6.10 to 7.04, system doesn't boot..."
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by cet.junior on 2007-04-23
[FONT="Verdana"][SIZE="2"]Hello,

Ubuntu is my main distro since jan/2006. I started with breezy and so on...'till feisty...

2 days ago, I had a (physical) problem with one of my HDD and lost all of my files. With nothing left to lose, I have formatted and reinstalled everything. Windows XP Professional first ('cause I need for some programs), in hda1, and also reinstalled and updated edgy (hda5=swap; hda6=/; hda7=/home).

After have finished all the edgy updates, I decided to upgrade to feisty, with the Update Manager. Everything was ok...downloaded around 600MB, installed, all of this with nothing running on background, just the Update Manager. At the end of the update, the systems asks me to reboot, to finish it...then, I reboot, just like asked...

Rebooting...the grub was ok, all kernels were listed, including the ones of edgy...I choosed the feisty one (2.6.20-15-386 and 2.6.20-15-generic)...now, here is the problem...passing the grub, the system hangs, with a bit of progress... Logically, I restarted the system and entered in the recovery mode of the kernel, and saw where it hangs..."Waiting for root filesystem" message...

I've searched the forum and saw many solutions...none worked. I have the option to format and reinstall feisty again (by the way, I'm downloading the iso now - this is why I've done the internet upgrade), but I really want to know what this problem is, and how to solve it.

My HDDs are IDE, and I know that is SATA driver that controls the disks now, so, the HDD must show something like sdx, right? I've tried many of the solutions in the forum, including change/edit grub menu.lst (and device.map) config from hdx to sdx, from hdx to UUID and vice-versa...and I've done the same with fstab, with no success...

I'm using Windows now, with EXT driver, so I can see (and edit) my (and system) files in linux partitions. If anyone can help me, thanks...:) 

SOU BRASILEIRO, então...se puder responder em PT-BR, melhor...meu inglês é arranhado pacas!!!:P

=============================
> My computer config:

ASUS A7V8X-X
Sempron 2600+ (1.8GHz), 512MB RAM
NVDIA GForce 2 MX400
40GB Samsung SP0411N (4 partitions, hda1=NTFS=Windows, hda2=EXTENDED, hda5=swap, hda6=EXT3=/, hda7=EXT3=/home)
=============================
> My Grub config (cutted out the comments):


default		0

timeout		10

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=FF6A34505D404EAF91FD4F7E3768D063 ro quiet splash locale=pt_BR
initrd		/boot/initrd.img-2.6.20-15-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=FF6A34505D404EAF91FD4F7E3768D063 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=FF6A34505D404EAF91FD4F7E3768D063 ro quiet splash locale=pt_BR
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=FF6A34505D404EAF91FD4F7E3768D063 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
=============================
> Grub device.map:

(hd0)	/dev/sda[/SIZE][/FONT]
=============================
My fstab:


[FONT="Lucida Console"][SIZE="1"]> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 (sda6) UUID=ff6a3450-5d40-4eaf-91fd-4f7e3768d063
UUID=FF6A34505D404EAF91FD4F7E3768D063 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7 (sda7) UUID=84b52d8c-2338-490d-8ccc-5578b99f8356
UUID=84B52D8C2338490D8CCC5578B99F8356 /home           ext3    defaults        0       2
# /dev/hda1 (sda1) UUID=701817271816EC3A
UUID=701817271816EC3A /media/hda1     ntfs    defaults,nls=utf8,umask=000,gid=46 0       1
# /dev/hda5 (sda5) UUID=c2738f1e-4116-4850-8757-d0ef07012a49
UUID=C2738F1E411648508757D0EF07012A49 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/SIZE][/FONT]
=============================

So...it's simple...I just want to boot my new feisty!!!:lolflag: 

Thanks for every help!!!
[/SIZE][/FONT]

---

### Post by cet.junior on 2007-04-23
By the way...I've tryed writing the UUID in many ways too, like capital letters (as showed above), without "-" and other...with no success either... :(

---

### Post by bgpete on 2007-04-23
I have had the same issue.   For me switching to the generic kernel allowed me to boot.  However, I cannot boot into any of the kernels that aren't "generic",  including the older kernels from 6.10.

==========================================================================================
lspci -vnn

00:00.0 Host bridge [0600]: Intel Corporation E7505 Memory Controller Hub [8086:2550] (rev 03)
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation E7505/E7205 PCI-to-AGP Bridge [8086:2552] (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: ff800000-ff9fffff
        Prefetchable memory behind bridge: e8000000-f7ffffff
        Capabilities: <access denied>

00:02.0 PCI bridge [0604]: Intel Corporation E7505 Hub Interface B PCI-to-PCI Bridge [8086:2553] (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ff400000-ff7fffff

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff40 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at ffa20800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at 88000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
        Subsystem: Dell Unknown device [1028:012d]
        Flags: medium devsel, IRQ 11
        I/O ports at cc80 [size=32]

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at c800 [size=256]
        I/O ports at cc40 [size=64]
        Memory at ffa20400 (32-bit, non-prefetchable) [size=512]
        Memory at ffa20000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon R300 NG [FireGL X1] [1002:4e47] (rev 80) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device [1002:0172]
        Flags: bus master, stepping, 66MHz, medium devsel, latency 255, IRQ 11
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at ec00 [size=256]
        Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ff800000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller [0380]: ATI Technologies Inc Radeon R300 [FireGL X1] (Secondary) [1002:4e67] (rev 80)
        Subsystem: ATI Technologies Inc Unknown device [1002:0173]
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at ff8e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:1c.0 PIC [0800]: Intel Corporation 82870P2 P64H2 I/OxAPIC [8086:1461] (rev 04) (prog-if 20 [IO(X)-APIC])
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at ff4ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:1d.0 PCI bridge [0604]: Intel Corporation 82870P2 P64H2 Hub PCI Bridge [8086:1460] (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ff600000-ff7fffff
        Capabilities: <access denied>

02:1e.0 PIC [0800]: Intel Corporation 82870P2 P64H2 I/OxAPIC [8086:1461] (rev 04) (prog-if 20 [IO(X)-APIC])
        Subsystem: Dell Unknown device [1028:012d]
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at ff4fe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:1f.0 PCI bridge [0604]: Intel Corporation 82870P2 P64H2 Hub PCI Bridge [8086:1460] (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=02, secondary=04, subordinate=04, sec-latency=64
        Capabilities: <access denied>

03:0e.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
        Subsystem: Dell Unknown device [1028:012c]
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at ff6e0000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at dcc0 [size=64]
        Capabilities: <access denied>

=======================================================================================
grub:
default		0

timeout		3

hiddenmenu


title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

=======================================================================================
less /proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 2.40GHz
stepping        : 7
cpu MHz         : 2392.265
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips        : 4788.17
clflush size    : 64

=======================================================================================
less /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d87d50b3-a307-46d0-9c70-b2c03ce68bf7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=485bdb9d-d6da-433f-9c22-b43d9015a38b none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


I am currently running but it's fairly clear there is an issue or at least potential for issues with the released Feisty.

---

### Post by cet.junior on 2007-04-23
> **bgpete said:**
> I have had the same issue.   For me switching to the generic kernel allowed me to boot.  However, I cannot boot into any of the kernels that aren't "generic",  including the older kernels from 6.10.

I am currently running but it's fairly clear there is an issue or at least potential for issues with the released Feisty.

I've tried the generic kernel too...no success with me...

And, I agree with you...and I think the kernel changes made a potential issue...

Will someone help the Ubuntu community with this issue?! Who knows... :P

PS.: Sorry about my english...it's a bit rusty... :lolflag:

---

### Post by cet.junior on 2007-04-23
Anyone?!:confused: :confused: :confused:

---

### Post by bgpete on 2007-04-23
Does Grub list any previous kernels?  Have you tried any other than the new one?

---

### Post by illogico on 2007-04-23
I have the same problem.
After upgrade to Festy, boot doesn't start.
It still after "Time: acpi_pm clocksource ..."

Can anyone help me?
thanks!

---

### Post by cet.junior on 2007-04-23
> **bgpete said:**
> Does Grub list any previous kernels?  Have you tried any other than the new one?

Yes...it lists all of the kernels, from edgy (and it updates) to the last kernel installed (of feisty upgrade).

Saying again...I can format the system and reinstall everything, but I want to know what is causing this...it's a critical bug of feisty, and many people are being affected by it...if someone can help, he/she will be helping not only me, but the entire community, and future versions of Ubuntu...

Thanks!

---

### Post by cet.junior on 2007-04-24
Any idea?:confused:

---

### Post by AndrewB on 2007-04-24
I ran the smart update last night...it wasn't.

Left me with a non bootable system. So I ran 7.10 from a live disk I had set aside.

Luckily I had set up the pc with seperate HDD for root and home

the new install tools from 7.04 are great.

I was able to format my root without touching home

then ran an install targeted to root on hda

30 minutes later, up and running. an hour after than had all my software up and running from home

overall a much better upgrade than from hoary to breezy or breezy to edgy.

though one of these days need to learn not to upgrade when there is no reason other than 'just doing it' for ha-ha's

Andrew

---

### Post by cet.junior on 2007-04-24
> **AndrewB said:**
> I ran the smart update last night...it wasn't.

Left me with a non bootable system. So I ran 7.10 from a live disk I had set aside.

Luckily I had set up the pc with seperate HDD for root and home

the new install tools from 7.04 are great.

I was able to format my root without touching home

then ran an install targeted to root on hda

30 minutes later, up and running. an hour after than had all my software up and running from home

overall a much better upgrade than from hoary to breezy or breezy to edgy.

though one of these days need to learn not to upgrade when there is no reason other than 'just doing it' for ha-ha's

Andrew

Thanks Andrew,

I choosed to reinstall everything...

A critical bug, with no correction ('till now, I guess?!)...overall, Ubuntu rules!!!:KS:KS:KS

Thanks everyone...:)

---

### Post by victor_c26 on 2007-05-06
So there isn't ever going to be a fix for this?

I really don't want to format my hard drive again.

---

