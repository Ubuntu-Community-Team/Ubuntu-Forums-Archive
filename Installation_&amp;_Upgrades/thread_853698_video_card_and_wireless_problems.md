---
title: "video card and wireless problems"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by ShabamJenkins on 2008-07-08
I have been having some problems after the most recent 8.04 update. I have a presario F756NR and am having some troubles getting a few things that were working pre-update to work again. To begin with I am very new to the linux world. I immediately swapped vista with the help of a friend. He got almost all the kinks worked out for me, so I'm not really sure what he did to get them to work. After the update however, my video card and wireless are no longer working. After doing some searching I found envyng. I installed and ran it, installing the drivers that it found automatically for me. All seemed to be working, restarted and enabled it through the hardware drivers option under administration, but still am having horrible resolution and an error during its boot. As for the wireless I have no idea what my friend originally used to get it working. Any help is greatly appreciated!

---

### Post by overdrank on 2008-07-08
> **ShabamJenkins said:**
> I have been having some problems after the most recent 8.04 update. I have a presario F756NR and am having some troubles getting a few things that were working pre-update to work again. To begin with I am very new to the linux world. I immediately swapped vista with the help of a friend. He got almost all the kinks worked out for me, so I'm not really sure what he did to get them to work. After the update however, my video card and wireless are no longer working. After doing some searching I found envyng. I installed and ran it, installing the drivers that it found automatically for me. All seemed to be working, restarted and enabled it through the hardware drivers option under administration, but still am having horrible resolution and an error during its boot. As for the wireless I have no idea what my friend originally used to get it working. Any help is greatly appreciated!

Hi and welcome, could you give us some system specs? You can use the command ```
lspci
``` and this will identify your hardware and maybe we can help.

---

### Post by ShabamJenkins on 2008-07-09
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

---

### Post by overdrank on 2008-07-09
> **ShabamJenkins said:**
> ```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
[COLOR="Blue"]00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)[/COLOR]
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
[COLOR="Red"]03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/COLOR]
```

Hi and sorry for the delay response, I have highlighted your graphics card in blue and the wireless in red. You can try and use the nvidia settings to adjust your resolutions. Use the alt, F2 keys and enter the command ```
gksu nvidia-settings
``` if you do not have the nvidia settings install you can search and install from synaptic manager. As for the wireless card you can search the forums and I sure find some help. If not the make a post in the Networking & Wireless forum. Good luck!:KS

---

### Post by ShabamJenkins on 2008-07-09
> Hi and sorry for the delay response, I have highlighted your graphics card in blue and the wireless in red. You can try and use the nvidia settings to adjust your resolutions. Use the alt, F2 keys and enter the command
Code:

gksu nvidia-settings

if you do not have the nvidia settings install you can search and install from synaptic manager. As for the wireless card you can search the forums and I sure find some help. If not the make a post in the Networking & Wireless forum. Good luck!

I searched under synaptic manager for the nvidia settings install and it's already there. I try the code above and get an error saying "you do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (ust run 'nvidia-xconfig; as root), and restart the X server".

---

### Post by yazuki101 on 2008-07-13
I am having the same issue with my acer aspire laptop. I have the exact same GPU (7000M) and receive the same *"you do not appear to be using the NVIDIA X driver. Please edit your X configuration file (ust run 'nvidia-xconfig; as root), and restart the X server"* message.

I still have yet to find anything regarding getting past this point. Hopefully someone will help us soon. :)

---

### Post by PmDematagoda on 2008-07-13
Run:-
```
sudo nvidia-xconfig
```
and see if that fixes it.

---

### Post by ShabamJenkins on 2008-07-13
> **PmDematagoda said:**
> Run:-
```
sudo nvidia-xconfig
```
and see if that fixes it.

```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

After running this that is what I get in return. I checked the NVIDIA X Server Settings again and get the same error message that i got from before. I am completely lost on what to try next.

---

### Post by ShabamJenkins on 2008-07-20
If anyone has any suggestions, I'm willing to try anything! I've been searching for answers forever it seems and have gotten nowhere.

---

### Post by ShabamJenkins on 2008-08-03
I've searched and searched for seems like ages and have yet to find a solution...anyone out there please help me!

---

### Post by PmDematagoda on 2008-08-04
Ok, can you post the output of:-
```
lsmod
```

---

### Post by ShabamJenkins on 2008-08-05
```
koori@koori-laptop:~$ lsmod
Module                  Size  Used by
af_packet              24840  2 
ipv6                  273892  10 
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
button                  8976  0 
battery                11012  0 
video                  18060  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
iptable_filter          3968  0 
ip_tables              13924  1 iptable_filter
x_tables               16260  1 ip_tables
aes_i586               34304  0 
dm_crypt               14984  0 
dm_mod                 58816  1 dm_crypt
ac                      6148  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263840  3 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               8068  0 
sdhci                  18828  0 
nvidia               7822336  0 
i2c_core               26112  1 nvidia
mmc_core               28420  1 sdhci
ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci
pcspkr                  4224  0 
agpgart                35016  1 nvidia
psmouse                39952  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
k8temp                  6656  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
forcedeth              51592  0 
ahci                   23300  2 
ata_generic             8452  0 
libata                125168  2 ahci,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  3 ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

### Post by ShabamJenkins on 2008-08-21
Is that the info that you wanted?

---

### Post by ShabamJenkins on 2008-08-29
Did I post that correctly?

---

### Post by ShabamJenkins on 2008-09-06
Anyone have any suggestions? I haven't got a chance to use ubuntu in so long now...it's depressing

---

### Post by ShabamJenkins on 2008-09-07
After messing around a little tonight and getting the latest updates, I think the driver is successfully installed although when I go to the NVIDIA X Server Settings I cannot fully see the screen. I have seen that the frontend resolution is 640x480 and the backend resolution is 1280x800. If I go to screen resolution the highest option that I have is 640x480. Is there a setting that needs to be changed somewhere to get the max up to the backend resolution? I could really use some help on this, I miss using ubuntu on here!

---

