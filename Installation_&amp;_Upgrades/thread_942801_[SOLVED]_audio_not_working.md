---
title: "[SOLVED] audio not working"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by brydong on 2008-10-09
I have a new installation on a dell vostro 200 and I have no audio working. I have headphones plugged into the front speaker port and get nothing. Looking for help to troubleshoot. I'm pasting output from my lspci if that helps...

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3600 Series
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

---

### Post by forger on 2008-10-09
1) what happens when you use the back speaker port?
2) did you try system > preferences > sound
3) did you try applications > sound&video > volume control
if volume control is not there, run in terminal:
```
gnome-volume-control
```

---

### Post by brydong on 2008-10-09
I have tried all those options and nothing. I also played with most, or all, settings in gnome-volume-control with no success...

---

### Post by forger on 2008-10-10
can you paste the output of:
```
sudo lshw -C multimedia
sudo lsmod
```

Set everything to pulseaudio in system > preferences > sound, press close and restart your computer.
Try the same for ALSA or OSS, but every time you press close and restart your machine.
After each restart, do you have sound at all?

---

### Post by brydong on 2008-10-10
*-multimedia            
       description: Audio device
       product: RV635 Audio device [Radeon HD 3600 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by brydong on 2008-10-10
Module                  Size  Used by
e1000e                 97828  0 
joydev                 13120  0 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ipv6                  267780  21 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  2 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
evdev                  13056  4 
snd_hda_intel         359192  3 
fglrx                1555468  24 
psmouse                40336  0 
dcdbas                  9504  0 
snd_seq_dummy           4996  0 
snd_hwdep              10628  1 snd_hda_intel
serio_raw               7940  0 
snd_seq_oss            35456  0 
snd_seq_midi            9504  0 
snd_pcm_oss            42528  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                78852  2 snd_hda_intel,snd_pcm_oss
snd_timer              24964  2 snd_seq,snd_pcm
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    57124  17 snd_hda_intel,snd_seq_dummy,snd_hwdep,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq,snd_pcm,snd_timer,snd_seq_device
button                  9232  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  0 
agpgart                34760  2 fglrx,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 31872  0 
hid                    38784  1 usbhid
floppy                 59588  0 
ahci                   28420  2 
libata                159344  1 ahci
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by brydong on 2008-10-16
anyone?? This is still an issue so any troubleshooting advice greatly appreciated.

---

### Post by StOoZ on 2008-10-16
this might solve your problem 
[http://ubuntuforums.org/showthread.php?t=940689]("http://ubuntuforums.org/showthread.php?t=940689")

---

### Post by brydong on 2008-10-16
thanks for the suggestion, didn't make a difference here....

---

### Post by brydong on 2008-10-17
I managed to find a fix on this thread... [http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)

the solution

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

---

