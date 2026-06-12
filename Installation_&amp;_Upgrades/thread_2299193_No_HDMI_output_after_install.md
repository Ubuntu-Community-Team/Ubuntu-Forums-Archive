---
title: "No HDMI output after install"
date: 2015-10-16
forum: Installation &amp; Upgrades
---

### Post by David_Andrew on 2015-10-16
Hi, I have been trying the live disc of xubuntu 14.04.3 for the past couple of days and today decided to install to hdd. Whilst running the live system I have had no problems with HDMI output (simply had to plug the cable in and enable the display in the display settings) but upon installing I am getting no output to the HDMI TV yet everything in the display settings seems exactly the same as it was on the live system.

Hoping somebody will be able to help me with this :p

Thanks in advance,

Dave.

---

### Post by TheFu on 2015-10-17
lxrandr - toggle the HDMI output checkbox. There are other versions of the same tool. xrandr and if you run ubuntu desktop there is a tool in there somewhere.

---

### Post by David_Andrew on 2015-10-17
> **TheFu said:**
> lxrandr - toggle the HDMI output checkbox. There are other versions of the same tool. xrandr and if you run ubuntu desktop there is a tool in there somewhere.

Tried that but still no display output to my HDMI (works if booting to live still though!) Thanks for the reply though :p

---

### Post by TheFu on 2015-10-17
Ah... let's find out which driver is loaded. Please post the output from :
[B]sudo lshw -C  video
[/B]

You said it didn't work. Can you be more specific?  Was there a toggle?  Did the apply work?

---

### Post by David_Andrew on 2015-10-17
> **TheFu said:**
> Ah... let's find out which driver is loaded. Please post the output from :
[B]sudo lshw -C  video
[/B]

You said it didn't work. Can you be more specific?  Was there a toggle?  Did the apply work?

There was a toggle which was already checked as enabled. I unchecked it,  clicked apply and then rechecked and clicked apply but no change to my  HDMI display, the lxrandr window just closes.

The ouput from sudo lshw -C video is:

  ```
 *-display
       description: VGA compatible controller
       product: C77 [GeForce 8200M G]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:20 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff 
```


For reference, the output on the live system is:

  ```
 *-display
       description: VGA compatible controller
       product: C77 [GeForce 8200M G]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:20 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff 
```

---

### Post by TheFu on 2015-10-17
Brilliant idea to run the command live-boot and on the install! 
What this shows is that the same driver is being used. That means it is just a setting somewhere.

```
$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

This is my chromebook output. No HDMI connection currently. 

[https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html](https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html) is specific to displays. I don't use unity, so don't have the ability check the actual display setting options.

---

### Post by David_Andrew on 2015-10-17
> **TheFu said:**
> Brilliant idea to run the command live-boot and on the install! 
What this shows is that the same driver is being used. That means it is just a setting somewhere.

```
$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

This is my chromebook output. No HDMI connection currently. 

[https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html](https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html) is specific to displays. I don't use unity, so don't have the ability check the actual display setting options.

Followed the link you provided and checked the display settings - both displays are set to active.

xrandr output for installed system is:

```

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS-1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 820mm x 461mm
   1360x768       60.0*+
   1920x1080i     60.1     50.0     60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  

```


and for the live system:

```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0 +
   1024x768       59.9* 
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 820mm x 461mm
   1360x768       60.0 +
   1920x1080i     60.1     50.0     60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1

```

---

### Post by TheFu on 2015-10-17
The mode used with the working HDMI is:
> 1024x768 75.1 70.1 60.0* 
Can you select that mode through the GUI?

---

### Post by David_Andrew on 2015-10-17
> **TheFu said:**
> The mode used with the working HDMI is:

Can you select that mode through the GUI?

Yes, I'm able to select that mode using the GUI but, alas, still nothing :razz:

---

### Post by David_Andrew on 2015-10-17
Don't know if this is helpful or not but here is the lsmod output:

installed:

```
Module                  Size  Used by
ctr                    16384  3 
ccm                    20480  3 
snd_hda_codec_hdmi     49152  1 
arc4                   16384  2 
snd_hda_codec_conexant    24576  1 
snd_hda_codec_generic    65536  1 snd_hda_codec_conexant
snd_hda_intel          32768  5 
ath5k                 135168  0 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
ath                    24576  1 ath5k
snd_hwdep              16384  1 snd_hda_codec
hp_wmi                 16384  0 
snd_pcm                94208  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
sparse_keymap          16384  1 hp_wmi
mac80211              618496  1 ath5k
nouveau              1208320  3 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
mxm_wmi                16384  1 nouveau
ttm                    86016  1 nouveau
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper        114688  1 nouveau
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
drm                   282624  6 ttm,drm_kms_helper,nouveau
rfcomm                 61440  4 
bnep                   20480  2 
bluetooth             430080  10 bnep,rfcomm
joydev                 20480  0 
snd                    69632  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0 
cfg80211              450560  3 ath,ath5k,mac80211
i2c_algo_bit           16384  1 nouveau
k10temp                16384  0 
shpchp                 32768  0 
soundcore              16384  2 snd,snd_hda_codec
video                  20480  1 nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau
i2c_nforce2            16384  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
pata_acpi              16384  0 
ums_realtek            20480  0 
uas                    24576  0 
usb_storage            57344  2 uas,ums_realtek
ahci                   32768  2 
psmouse               102400  0 
forcedeth              65536  0 
libahci                32768  1 ahci
pata_amd               16384  0 
``` 


live system:

```
Module                  Size  Used by
arc4                   16384  2 
snd_hda_codec_hdmi     49152  1 
snd_hda_codec_conexant    24576  1 
hp_wmi                 16384  0 
snd_hda_codec_generic    65536  1 snd_hda_codec_conexant
sparse_keymap          16384  1 hp_wmi
dm_crypt               24576  0 
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ath5k                 135168  0 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
ath                    24576  1 ath5k
snd_rawmidi            28672  1 snd_seq_midi
mac80211              618496  1 ath5k
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 20480  0 
dm_multipath           24576  0 
cfg80211              450560  3 ath,ath5k,mac80211
snd_timer              28672  2 snd_pcm,snd_seq
scsi_dh                16384  1 dm_multipath
serio_raw              16384  0 
snd                    69632  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
k10temp                16384  0 
shpchp                 32768  0 
soundcore              16384  2 snd,snd_hda_codec
rfcomm                 61440  4 
bnep                   20480  2 
bluetooth             430080  10 bnep,rfcomm
i2c_nforce2            16384  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
squashfs               49152  1 
overlay                36864  1 
nls_iso8859_1          16384  2 
dm_mirror              24576  0 
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
nouveau              1208320  3 
mxm_wmi                16384  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    86016  1 nouveau
pata_acpi              16384  0 
drm_kms_helper        114688  1 nouveau
ums_realtek            20480  0 
psmouse               102400  0 
drm                   282624  6 ttm,drm_kms_helper,nouveau
ahci                   32768  1 
uas                    24576  0 
libahci                32768  1 ahci
forcedeth              65536  0 
usb_storage            57344  4 uas,ums_realtek
pata_amd               16384  0 
video                  20480  1 nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau 
```

---

### Post by TheFu on 2015-10-17
**code tags** would be helpful. [http://blog.jdpfu.com/code_tags](http://blog.jdpfu.com/code_tags)   <---- redirects to a guide here.
I'm clueless on what to try next. Sorry.

---

### Post by David_Andrew on 2015-10-18
> **TheFu said:**
> **code tags** would be helpful. [http://blog.jdpfu.com/code_tags](http://blog.jdpfu.com/code_tags)   <---- redirects to a guide here.
I'm clueless on what to try next. Sorry.

Code tags added ;)

No worries, thanks for the help. :p

---

### Post by Nibblyn on 2016-09-20
You may also want to consider using Grub Legacy instead of Grub2 if your case is similar to that reported here:

HDMI works with Live Iso but not with installed OS:
[https://ubuntuforums.org/showthread.php?t=2334805](https://ubuntuforums.org/showthread.php?t=2334805)

HDMI works with Grub Legacy but not with Grub2:
[https://ubuntuforums.org/showthread.php?t=2335950](https://ubuntuforums.org/showthread.php?t=2335950)

Please report back if this solves the issue for you. Thanks.

---

### Post by oldos2er on 2016-09-20
Old thread closed.

---

