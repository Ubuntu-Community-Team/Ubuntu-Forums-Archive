---
title: "acpi-cpufreq not working in 2.6.22-14-generic on Intel(R) Pentiium M"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by depo24 on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154124/comments/1](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154124/comments/1) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

Recently upgraded to gutsy from feisty and the problems started. Cant get frequency scaling to work.
Both acpi-cpufreq.ko and speedstep-centrino.ko gives error "No such device". Tried applying linux-phc-0.3.0, no luck.
Read somewhere that disabling "Long battery mode" in bios solves problem for acpi-cpufreq.ko, but for me it didn't change a think.
Frequency scaling worked fine with 2.6.20-16-generic using speedstep-centrino module. Its Fujitsu-siemens Amilo M m3438g.
Actually , making processor work at full speed its enough for me, because now its just 800. No modules, responsible for frequency scaling, are loaded, no software like cpudyn, powernowd or cpufreq are installed, but still 800
After modprobing acpi-cpufreq.ko and speedstep-centrino.ko dmesg reports:
[ 214.240000] speedstep_centrino: no version for "struct_module" found: kernel tainted.

root@Hell:/home/kiero# uname -a
Linux Hell 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

root@Hell:/home/kiero# cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 13
model name : Intel(R) Pentium(R) M processor 2.00GHz
stepping : 8
cpu MHz : 800.065
cache size : 2048 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips : 1616.27
clflush size : 64

root@Hell:/home/kiero# lsmod
Module Size Used by
ipv6 273892 8
af_packet 24840 2
binfmt_misc 12936 1
rfcomm 42136 2
l2cap 26240 11 rfcomm
bluetooth 57060 4 rfcomm,l2cap
ppdev 10244 0
video 18060 14
battery 11012 3
container 5504 0
sbs 19592 0
button 8976 0
dock 10656 0
ac 6148 0
sbp2 24072 0
parport_pc 37412 0
lp 12580 0
parport 37448 3 ppdev,parport_pc,lp
pcspkr 4224 0
snd_hda_intel 263712 0
snd_pcm_oss 44672 0
snd_mixer_oss 17664 1 snd_pcm_oss
snd_pcm 80388 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 33152 0
ipw2200 149320 0
psmouse 39952 0
serio_raw 8068 0
snd_seq_midi 9600 0
snd_rawmidi 25728 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
xpad 9988 0
nvidia 6221776 26
ieee80211 35656 1 ipw2200
ieee80211_crypt 7040 1 ieee80211
iTCO_wdt 11940 0
iTCO_vendor_support 4868 1 iTCO_wdt
snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_core 26112 1 nvidia
snd_timer 24324 2 snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp 25620 0
snd 54660 9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8800 1 snd
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm
shpchp 34580 0
pci_hotplug 32704 1 shpchp
agpgart 35016 2 nvidia,intel_agp
joydev 11328 0
evdev 11136 8
reiserfs 248704 1
sr_mod 17828 0
cdrom 37536 1 sr_mod
sg 36764 0
sd_mod 30336 6
ata_piix 17540 0
usbhid 29536 0
hid 28928 1 usbhid
sata_via 12548 4
r8169 32260 0
ohci1394 36528 0
ieee1394 96312 2 sbp2,ohci1394
ata_generic 8452 0
libata 125168 3 ata_piix,sata_via,ata_generic
scsi_mod 147084 5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd 36492 0
uhci_hcd 26640 0
usbcore 138632 5 xpad,usbhid,ehci_hcd,uhci_hcd
thermal 14344 3
processor 32072 1 thermal
fan 5764 0
fuse 47124 5
apparmor 40728 0
commoncap 8320 1 apparmor

---

