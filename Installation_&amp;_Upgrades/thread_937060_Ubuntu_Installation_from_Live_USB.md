---
title: "Ubuntu Installation from Live USB"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by nebu on 2008-10-03
I created a live usb using the live cd iso >>>

now when i try running the live usb.... it runs fine till i try to install ubuntu>>>

then when i have to run the partition editor.... my hard disk(500gig ATA) is not 
recognized.... the only thing in the list of locations where ubuntu can be installed is
my usb pen drive from which i am running the live usb:confused::confused::confused:

btw... i already have winxp and vista running on dual boot.... is that screwing up the live usb??

how do i fix this problem

---

### Post by zindine on 2008-10-03
You seem to know a little about Ubuntu so I won't put too much details, but have you tried to open a terminal and use the regular tools (like fdisk for example) to see if your drive is recognized by the kernel? 

Also, using lspci and lsmod, you can check that your storage subsystem is recognized and modules have been loaded. 

Get back here with some of the output of all that so we can help you better.

---

### Post by nebu on 2008-10-03
this is what i get with *lspci* ....
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation ICH10 PCI Express Port 2
00:1c.5 PCI bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation ICH10 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
00:1f.5 IDE interface: Intel Corporation ICH10 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
01:00.1 Audio device: ATI Technologies Inc Unknown device aa30
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

this is what i get with *lsmod*......
```

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  267780  14 
af_packet              23812  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
lp                     12324  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
ac                      6916  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
evdev                  13056  3 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
psmouse                40336  0 
serio_raw               7940  0 
pcspkr                  4224  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
button                  9232  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
battery                14212  0 
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
sg                     36880  0 
sd_mod                 30720  2 
usb_storage            73664  1 
libusual               19108  1 usb_storage
pata_jmicron            7040  0 
pata_acpi               8320  0 
r8169                  32900  0 
ata_generic             8324  0 
libata                159344  3 pata_jmicron,pata_acpi,ata_generic
scsi_mod              151436  4 sg,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 


```

and when i do *fdisk -l* i get no output......

---

### Post by zindine on 2008-10-03
make sure you use sudo for fdisk or you won't get any output. 

I am looking at your other output and will get back to you hopefully.

---

### Post by zindine on 2008-10-03
Ok, it seems to be a known issue. Check this: [http://www.linuxquestions.org/questions/linux-hardware-18/sata-drive-not-detected-662096/](http://www.linuxquestions.org/questions/linux-hardware-18/sata-drive-not-detected-662096/)

Let me know if that works.

---

### Post by nebu on 2008-10-03
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 4110 MB, 4110417920 bytes
33 heads, 63 sectors/track, 3861 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3811     3960816    b  W95 FAT32
```

this is my usb drive not my HDD

---

