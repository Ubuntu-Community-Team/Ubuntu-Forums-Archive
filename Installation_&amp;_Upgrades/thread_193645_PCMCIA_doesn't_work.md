---
title: "PCMCIA doesn't work"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by 1002285 on 2006-06-10
After network upgrade from 5.10 to dapper, the PCMCIA no longer works.
At the startup I see "Starting PCMCIA services ... fails".
I found a thread about PCMCIA related hang, but I guess that is not my problem. It does not hang. And I need PCMCIA. I have 2 PCMCIA and 1 USB slot.
Can anybody help me to get them working?
Outputs of lspci and lsmod commands are here:

ml@DellUbuntu606:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ml@DellUbuntu606:~$ lsmod
Module                  Size  Used by
ipv6                  217408  6
snd                    48644  0
soundcore               9184  1 snd
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
ppdev                   9092  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
rtc                    11832  0
pcmcia                 24584  4
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
af_packet              20232  0
nls_iso8859_1           4224  1
vfat                   12288  1
fat                    46492  1 vfat
nls_cp437               5888  2
ntfs                   92016  1
dm_mod                 50364  1
md                     40656  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  3 ppdev,parport_pc,lp
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  6
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  488
fbcon                  34176  0
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0
commoncap               6784  1 capability

---

### Post by James Keating on 2006-06-10
This sounds like what happened to me. It seems common, and appears to be due to a kernel bug.

I tried many approaches, but the one that worked for me came from another Ubuntu thread, thanks to Daniel Carrera. The kernel disables the PCMCIA port during boot because nothing is using it then. You have to insert the modules by hand, then start cardmgr to watch the card.

sudo modprobe pcmcia && modprobe pcmcia_core
sudo cardmgr

Some people say you need to eject and insert the card after activating the modules, but I didn't need to.

---

### Post by 1002285 on 2006-06-12
Maybe it's not the same thing?
My results:

ml@DellUbuntu606:~$ sudo modprobe pcmcia && modprobe pcmcia_core
ml@DellUbuntu606:~$ sudo cardmgr
cardmgr[4867]: no sockets found!

And sound and usb wifi card don't work either (although the wifi doesn't work in 5.10 either)

---

### Post by shiellb on 2006-06-14
I just upgraded to DD6.06 and have a similar problem.  I get the pcmcia services "failed" and when I open any of the OOo suite I have funny shaped squares where buttons for "file" etc are located.  When I try to close the program down  the window to do so have the same little squares.  What happened and how do I fix it?  Thanks.  Shiellb:-({|=

---

