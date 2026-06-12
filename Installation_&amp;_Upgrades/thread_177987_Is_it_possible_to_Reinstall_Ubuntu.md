---
title: "Is it possible to Reinstall Ubuntu?"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by nanocosm on 2006-05-17
Hi!

Is it possible to Reinstall Ubuntu without loosing the currently installed packages/files/personal data ect... ?

I'm thinking of something like Windows-Repair-Mode.

My Problem is that I installed Ubuntu (Dapper) on my Notebook and then cloned the HDD to my Desktop. Well quite everything works fine, but for example the /sys/devices/system/cpu/cpu0/ dir is empty (acpi module will not load). I do not want to recompile the kernel nor editing modules (aka the gentoo-style)

Otherwise: Is there something that re-detects my hardware and installs the right kernel/modules and everything needed like the installer does?


Thanks for any help!

---

### Post by Sef on 2006-05-17
Try this:

sudo apt-get update

sudo apt-get install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

---

### Post by nocturn on 2006-05-17
[QUOTE=nanocosm]
Otherwise: Is there something that re-detects my hardware and installs the right kernel/modules and everything needed like the installer does?
[/QUOTE]

Most of this (except X) should be detected at each boot.  Not fixed by the installer.

So if it is not working, maybe there's another error, or your CPU does not have certain features.

---

### Post by nanocosm on 2006-05-18
[QUOTE=nocturn]Most of this (except X) should be detected at each boot.  Not fixed by the installer.

So if it is not working, maybe there's another error, or your CPU does not have certain features.[/QUOTE]


It has. And it worked fine with Gentoo. But I cannot remember which modules were loaded.

Here's my current lsmod and it seems that everything needed has been loaded but not used:
```
Module                  Size  Used by
binfmt_misc            12296  1
vmnet                  37284  12
vmmon                 111724  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_powersave       1920  0
cpufreq_stats           5636  0
cpufreq_userspace       4696  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
freq_table              4740  1 cpufreq_stats
tc1100_wmi              6916  0
video                  16260  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
container               4608  0
button                  6672  0
pcc_acpi               12416  0
sony_acpi               5516  0
ac                      5252  1 acpi_sbs
dev_acpi               11140  0
hotkey                 11556  0
ext2                   68360  1
dm_mod                 58936  1
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
ipv6                  265600  6
af_packet              22920  2
8139too                26880  0
8139cp                 22528  0
mii                     5888  2 8139too,8139cp
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
psmouse                36228  0
snd_intel8x0           33820  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
serio_raw               7300  0
snd_pcm_oss            53664  0
usblp                  13056  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89736  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
dsbr100                 6400  0
videodev                9856  1 dsbr100
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
floppy                 62148  0
pcspkr                  2180  0
rtc                    13492  0
tg3                   102020  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
nvidia               4545076  12
i2c_core               21904  2 i2c_acpi_ec,nvidia
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
tsdev                   8000  0
sg                     37920  0
evdev                   9856  2
usbhid                 38368  0
reiserfs              268016  2
ide_generic             1536  0
ehci_hcd               32008  0
ohci_hcd               21892  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33680  0
usbcore               129668  7 usblp,dsbr100,usbhid,ehci_hcd,ohci_hcd,uhci_hcd
sd_mod                 19984  6
ata_piix               11012  9
libata                 78992  1 ata_piix
scsi_mod              139496  5 sr_mod,sbp2,sg,sd_mod,libata
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13448  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

---

### Post by nanocosm on 2006-05-18
[QUOTE=nanocosm]... but for example the /sys/devices/system/cpu/cpu0/ dir is empty (acpi module will not load). I do not want to recompile the kernel nor editing modules (aka the gentoo-style)
[/QUOTE]


Adding ```
p4-clockmod
``` to /etc/modules made it. (al least this ;-)

---

