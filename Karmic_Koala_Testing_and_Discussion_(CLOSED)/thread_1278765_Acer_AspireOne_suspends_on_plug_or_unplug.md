---
title: "Acer AspireOne suspends on plug or unplug"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jdmpike on 2009-09-29
Hello all,

For quite some time now, my Acer AspireOne netbook has been suspending whenever I plug or unplug the device. I really want to figure out what is going on with this so I can plug/unplug my device without suspending...

I was able to monitor the output of lshal -m to capture the following:

```
Start monitoring devicelist:
-------------------------------------------------
21:10:39.377: computer_power_supply_battery_BAT0 property battery.remaining_time = 17514 (0x446a)
21:10:39.382: computer_power_supply_battery_BAT0 property battery.charge_level.rate = 8391 (0x20c7)
21:10:39.386: computer_power_supply_battery_BAT0 property battery.reporting.rate = 777 (0x309)
21:10:39.391: computer_power_supply_battery_BAT0 property battery.voltage.current = 11861 (0x2e55)
21:10:46.032: computer_power_supply_ac_adapter_AC property ac_adapter.present = true
```

Sure enough, when computer_power_supply_ac_adapter_AC property ac_adapter.present toggled to true, my device suspended.

This was logged in pm-suspend.log

```
Tue Sep 29 21:10:46 CDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux luckybook 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:51 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
ib_iser                31584  0 
rdma_cm                30140  1 ib_iser
ib_cm                  37196  1 rdma_cm
iw_cm                   8640  1 rdma_cm
ib_sa                  19812  2 rdma_cm,ib_cm
ib_mad                 37524  2 ib_cm,ib_sa
ib_core                57884  6 ib_iser,rdma_cm,ib_cm,iw_cm,ib_sa,ib_mad
ib_addr                 7936  1 rdma_cm
iscsi_tcp              11620  0 
libiscsi_tcp           16384  1 iscsi_tcp
libiscsi               39468  3 ib_iser,iscsi_tcp,libiscsi_tcp
scsi_transport_iscsi    30260  4 ib_iser,iscsi_tcp,libiscsi
aes_i586                8124  2 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203296  1 
fbcon                  36544  71 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
snd_hda_intel          26664  2 
snd_hda_codec          69276  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                 10272  0 
i915                  218824  3 
iptable_filter          3100  0 
uvcvideo               59080  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
videodev               36736  1 uvcvideo
arc4                    1660  2 
snd_seq_oss            28576  0 
ecb                     2524  2 
v4l1_compat            14496  2 uvcvideo,videodev
drm                   159584  3 i915
intel_agp              26684  1 
ath5k                 123940  0 
psmouse                56180  0 
mac80211              181236  1 ath5k
led_class               4096  1 ath5k
serio_raw               5280  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath                     8060  1 ath5k
i2c_algo_bit            5760  1 i915
agpgart                34988  2 drm,intel_agp
snd                    59204  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  3 ath5k,mac80211,ath
video                  19188  1 i915
output                  2780  1 video
lp                      8964  0 
parport                35340  2 ppdev,lp
atl1e                  31792  0 
             total       used       free     shared    buffers     cached
Mem:       2052072     591896    1460176          0      40088     310100
-/+ buffers/cache:     241708    1810364
Swap:      6008268          0    6008268
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: No PulseAudio daemon running, or not running as session daemon.
No PulseAudio daemon running, or not running as session daemon.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: Welcome to PulseAudio! Use "help" for usage information.
>>> >>> success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Tue Sep 29 21:10:48 CDT 2009: performing suspend
Tue Sep 29 21:10:56 CDT 2009: Awake.
Tue Sep 29 21:10:56 CDT 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Returned exit code 1.
/etc/pm/sleep.d/99laptop-mode resume suspend: Laptop mode disabled, not active
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: 
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254
success.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: No PulseAudio daemon running, or not running as session daemon.
No PulseAudio daemon running, or not running as session daemon.
success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: Welcome to PulseAudio! Use "help" for usage information.
>>> >>> success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
```

Thanks to anyone who can offer any help with the issue.

---

### Post by baloc on 2009-10-05
This problem seems to be linked to the "When laptop lid is closed" option in power management. When you set it to suspend, the computer will suspend after unplugging AC power. A simple workaround is to set the option to "blank screen," which is a lot faster to come out of than a suspend.

I've noticed other problems with suspend on the Aspire One. For example, if you hit Fn+F4 to suspend manually, it doesn't always work. The same thing for "put display to sleep when inactive" - the display won't go to sleep in certain circumstances. I haven't pinpointed the exact circumstances, but it seems to be linked to certain applications running in the background.

---

