---
title: "Help, my dapper is broken"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by the_mook on 2006-08-19
after I upgraded from Breezy, 
my cdrom, usb, sound card and wireless stop working !

I fixed my cdrom  problem by linking /dev/cdrom to /dev/hdc

but I still don't have /dev/dsp or /dev/sd# or wireless.

Here are the errors I have found in the dmesg:
> [4294676.915000] hub 3-0:1.0: USB hub found
[4294676.946000] ohci_hcd 0000:02:07.1: NEC Corporation USB (#2)
[4294676.946000] ohci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 4
[4294676.976000] hub 4-0:1.0: USB hub found
[4294677.130000] ehci_hcd 0000:02:07.2: NEC Corporation USB 2.0
[4294677.151000] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 5
[4294677.151000] ehci_hcd 0000:02:07.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294677.151000] hub 5-0:1.0: USB hub found


here is the output of lspci:
> 0000:00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
0000:02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:07.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

here is the output from lsmod:
> Module                  Size  Used by
snd_pcm_oss            46368  0
snd_pcm                78344  1 snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
sis900                 19456  0
nls_cp1255              5632  1
nls_cp437               5888  0
jfs                   157764  0
xfs                   499256  0
exportfs                5376  1 xfs
ext3                  115976  0
jbd                    48536  1 ext3
hfs                    42756  0
hfsplus                72708  0
vfat                   12288  0
fat                    46492  1 vfat
isofs                  32824  1
udf                    75524  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd                    48644  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9184  1 snd
rfcomm                 34972  1
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
af_packet              20232  2
radeon                 68352  0
drm                    58004  1 radeon
agpgart                32328  1 drm
ppdev                   9092  0
speedstep_lib           4228  0
cpufreq_powersave       1920  0
cpufreq_stats           5124  0
cpufreq_userspace       4444  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
freq_table              4484  1 cpufreq_stats
tc1100_wmi              6916  0
video                  16004  0
battery                 9604  0
container               4608  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
pcc_acpi               11392  0
sony_acpi               5516  0
ac                      4996  0
dev_acpi               11396  0
hotkey                  9508  0
genrtc                  8840  0
pcmcia                 24584  4
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
ipv6                  217408  13
nls_utf8                2176  1
ntfs                   92016  1
md                     40656  0
dm_mod                 50364  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  3 ppdev,parport_pc,lp
reiserfs              217200  2
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ehci_hcd               29448  0
8139cp                 18432  0
8139too                23552  0
mii                     5248  3 sis900,8139cp,8139too
ohci_hcd               18564  0
usbcore               104316  3 ehci_hcd,ohci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  6
ide_generic             1664  0
atiixp                  5648  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,atiixp
unix                   24624  761
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


HELP !

---

### Post by zxee on 2006-08-19
How did you go about the upgrade e,g, did you use an offcial guide?
There are several upgrade troubleshooting threads here: [http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Also it might be revealing to see the output of this command:> lsb_release -a

---

### Post by the_mook on 2006-08-19
After I update my sources.list with source-o-matic
Ijust run:
> sudo apt-get update
sudo apt-get dist-upgrade


and the output of "lsb_release -a" is:
> 
LSB Version:    core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:cxx-2.0-noarch:cxx-3.0-noarch:cxx-3.1-noarch:cxx-2.0-ia32:cxx-3.0-ia32:cxx-3.1-ia32:graphics-2.0-noarch:graphics-3.0-noarch:graphics-3.1-noarch:graphics-2.0-ia32:graphics-3.0-ia32:graphics-3.1-ia32:desktop-3.1-noarch:desktop-3.1-ia32
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper


---

### Post by the_mook on 2006-08-19
I fixed my sound problem, but my main problem is that usb doesn't work.

I don't know how to fixed it.

---

