---
title: "no parport device anymore after changing to kernel image 2.6.10-5"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by itsme on 2005-04-27
after changing the kernel image from 2.6.10-2 to 2.6.10-5 the devices parport0-3 disapeared from /dev/. 

ls mod shows:

Module                  Size  Used by
nls_cp437               5600  1 
ntfs                  110512  1 
sd_mod                 17776  2 
usb_storage            71936  0 
vmnet                  30460  14 
vmmon                 108364  3 
acpi_cpufreq            5956  1 
speedstep_lib           3940  0 
proc_intf               3908  0 
freq_table              4004  1 acpi_cpufreq
cpufreq_userspace       4348  1 
cpufreq_powersave       1632  0 
cpufreq_ondemand        6140  0 
pcmcia                 22244  4 
ipv6                  257888  17 
af_packet              21992  2 
ohci1394               34596  0 
yenta_socket           21344  0 
pcmcia_core            57984  2 pcmcia,yenta_socket
3c59x                  39112  0 
snd_intel8x0           32352  2 
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  1 
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  2 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
hw_random               5300  0 
usbhid                 31936  0 
uhci_hcd               32816  0 
usbcore               119000  4 usb_storage,usbhid,uhci_hcd
pci_hotplug            33488  0 
intel_agp              22140  1 
agpgart                33608  1 intel_agp
floppy                 58864  0 
pcspkr                  3496  0 
rtc                    12472  0 
md                     47440  0 
dm_mod                 59420  1 
capability              4648  0 
commoncap               7712  1 capability
evdev                   9344  0 
mousedev               11288  2 
tsdev                   7520  0 
sr_mod                 17188  0 
sbp2                   23816  1 
scsi_mod              127552  4 sd_mod,usb_storage,sr_mod,sbp2
ieee1394              108312  2 ohci1394,sbp2
psmouse                21320  0 
parport_pc             37252  1 
lp                     11144  0 
parport                36744  2 parport_pc,lp
ide_cd                 41700  1 
cdrom                  40220  2 sr_mod,ide_cd
xfs                   602424  4 
ide_generic             1312  0 
piix                   10340  1 
ide_disk               20416  6 
ide_core              129356  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   28276  824 
thermal                13320  0 
processor              22452  2 acpi_cpufreq,thermal
fan                     4388  0 
fbcon                  37504  0 
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  0 
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb

and messages shows:

Apr 27 07:15:31 xlmetgrz01012 kernel: parport: PnPBIOS parport detected.
Apr 27 07:15:31 xlmetgrz01012 kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 27 07:15:31 xlmetgrz01012 kernel: lp0: using parport0 (interrupt-driven).

so the parallel port is recogniced but no devices under /dev

any idea?

---

