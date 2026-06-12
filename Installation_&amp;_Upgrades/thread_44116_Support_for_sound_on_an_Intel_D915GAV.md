---
title: "Support for sound on an Intel D915GAV"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by bigmouth000 on 2005-06-24
Here's my config:

Intel 2.8Ghz Processor
120 Gb SATA HDD
Intel D915GAV Motherboard
512 MB Ram 

This is a 6 channel sound with 3 rear sound jacks and 2 in the front. When i see the device config, it shows Intel sound but nothing more than that. Is there in built support for this that I'm unable to use ? 

PS: Tried to install alsa .9 but it says something like 'alsa already in the kernel' does alsa support this sound on a motherboard ? What can be done ???

---

### Post by bigmouth000 on 2005-07-05
Is there still no answer for this ? 

The 915 chipset is more than a few months old. How is it that alsa doesn't recognize this and many distros just ignore the audio drivers ? I have a feeling i'm not alone with this problem !!

---

### Post by mingus on 2005-07-05
As a start, it would be advisable to search the Forums and also google it . . .

I found quite a few hits.  Appears there is support in ALSA 1.08 and the 2.6 kernel, which you have.  One user indicated it was working with OSS (an older alternative to ALSA).  The sound module is probably snd-intel8x0.

Try a few things.  In a terminal do:

$lspci
you should see the audio controller and the codec (like AC97)

$lsmod | more
you should see a half-dozen or so sound modules - look for the parent module, like snd-intel8x0.

$modinfo <module name>
will give you info on that module - snd-intel8x0 will not report the 915 but it is a general purpose AC97 driver.  You will also see any supported parameters.

$alsamixer
in the upper left you should see your card/chip.  Sometimes when the module is configured the audio is set at zero and all that's needed is for it to be turned up in the alsamixer

Go to System/Preferences/Multimedia Systems Selector, and check what the sound system setup is.  ESD is a service designed to manage multiple audio sources simulataneously, but there can be issues with it.  You can test it here.  And you can try Alsa or OSS.

Finally, in a terminal do:
$cd /etc/modprobe.d
$sudo gedit alsa-base
use Search to find your module; also take note whether it is in the Options section.  Some driver modules need parameters to work with a particular hw config.  If you see something in this section, the hw and needed parms were detected.

---

### Post by sanji on 2005-07-25
Thank's...I'll try its!

---------------------------------------------------------------------------------------------------------------------------------
sanjo@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev  04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Famil y Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. 82915G Express Chipset Family Graph ics Controller (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definiti on Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridg e (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
0000:06:02.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

----------------------------------------------------------------------------------------------------------------------------
sanjo@ubuntu:~$ lsmod
Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
vga16fb                12488  1
vgastate                8576  1 vga16fb
ipv6                  229504  9
af_packet              20744  2
8139too                24320  0
mii                     4736  1 8139too
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
ata_piix                8836  0
libata                 44548  1 ata_piix
scsi_mod              119936  1 libata
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd
pciehp                 83948  0
shpchp                 86116  0
pci_hotplug            30512  2 pciehp,shpchp
intel_agp              20636  1
agpgart                31784  1 intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
tsdev                   7488  0
evdev                   9088  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  663
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  2 vga16fb,vesafb
cfbimgblt               3072  2 vga16fb,vesafb
cfbfillrect             3584  2 vga16fb,vesafb
sanjo@ubuntu:~$

--------------------------------------------

Where the [COLOR=Blue]sound[/COLOR] module???

---

### Post by varunus on 2005-08-02
Here's how to configure sound for that chipset (at least, I think its that one):
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)

---

### Post by ekravche on 2005-09-02
Interesting I'll give this a try, and see whether it will work for me. Thanx for the info

---

