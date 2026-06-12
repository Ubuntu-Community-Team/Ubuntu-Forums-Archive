---
title: "Ubuntu 13.04 - no CPU scaling after resume"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by rigobot on 2013-05-12
Hi everyone,

before posting a new bug on launchpad I'm asking you for any suggestion. I noticed through turbostat that, after resuming my netbook from suspend, my cpu frequencies are stuck in the lowest value. I than installed the "indicator-cpufreq" to change governor which is for default set on ondemand, and actually changing to conservative I can notice againg the frequencies scaling.
But sadly, once I return to ondemand, the frequencies are fixed angain in the lowest value. If I reboot the machine everything works fine. With ubuntu 12.10 I did not have this behaviour.

Thank you!

My specs:
```

OS: Ubuntu 13.04 bit

CPU: Intel(R) Core(TM) i5-3320M

MODULES LOADED:
michael_mic            12612  8 
arc4                   12615  4 
bnep                   18036  2 
rfcomm                 42641  12 
binfmt_misc            17500  1 
nfsd                  248016  13 
auth_rpcgss            40632  1 nfsd
nfs_acl                12837  1 nfsd
nfs                   164047  0 
lockd                  76670  2 nfs,nfsd
sunrpc                235585  23 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                57430  1 nfs
snd_hda_codec_hdmi     36996  1 
snd_hda_codec_idt      50425  1 
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
snd_hda_intel          43715  3 
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec         188899  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
dell_wmi               12681  0 
ppdev                  17073  0 
sparse_keymap          13890  1 dell_wmi
parport_pc             28152  0 
lib80211_crypt_tkip    17379  0 
btusb                  22474  0 
wmi                    19070  1 dell_wmi
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i915                  600351  3 
mac_hid                13205  0 
video                  19390  1 i915
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
dell_laptop            17369  0 
bluetooth             228619  22 bnep,btusb,rfcomm
dcdbas                 14397  1 dell_laptop
wl                   2573614  0 
mei                    41158  0 
i2c_algo_bit           13413  1 i915
psmouse                95870  0 
msr                    12908  0 
lpc_ich                17061  0 
serio_raw              13215  1 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
lib80211               14352  2 wl,lib80211_crypt_tkip
microcode              22881  0 
tg3                   153796  0 
ptp                    18621  1 tg3
pps_core               14080  1 ptp
ahci                   25731  3 
libahci                31364  1 ahci
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
```

---

### Post by Doug S on 2013-05-13
It seems odd that conservative mode would work yet ondemand mode wouldn't. I wonder if some parameter for ondemand mode got corrupted. Perhaps look around at the settings and such, without using any intermediate tool. Example (not being sure what we are looking for):```
doug@s15:~/temp$ [COLOR=#ff0000]ls -l /sys/devices/system/cpu/cpu0/cpufreq[/COLOR]
total 0
-r--r--r-- 1 root root 4096 May 12 08:13 affected_cpus
-r--r--r-- 1 root root 4096 May 12 08:13 bios_limit
-r-------- 1 root root 4096 May 12 08:13 cpuinfo_cur_freq
-r--r--r-- 1 root root 4096 May 12 08:13 cpuinfo_max_freq
-r--r--r-- 1 root root 4096 May 12 08:13 cpuinfo_min_freq
-r--r--r-- 1 root root 4096 May 12 08:13 cpuinfo_transition_latency
-r--r--r-- 1 root root 4096 May 12 08:13 related_cpus
-r--r--r-- 1 root root 4096 May 12 08:13 scaling_available_frequencies
-r--r--r-- 1 root root 4096 May 12 08:13 scaling_available_governors
-r--r--r-- 1 root root 4096 May 12 08:13 scaling_cur_freq
-r--r--r-- 1 root root 4096 May 12 08:13 scaling_driver
-rw-r--r-- 1 root root 4096 May  4 14:24 scaling_governor
-rw-r--r-- 1 root root 4096 May 12 08:13 scaling_max_freq
-rw-r--r-- 1 root root 4096 May 12 08:13 scaling_min_freq
-rw-r--r-- 1 root root 4096 May 12 08:13 scaling_setspeed
drwxr-xr-x 2 root root    0 May 12 08:13 stats
doug@s15:~/temp$ [COLOR=#ff0000]sudo cat /sys/devices/system/cpu/cpu0/cpufreq/*[/COLOR]
[sudo] password for doug:
0
3401000
3401000
3401000
1600000
10000
0 1 2 3 4 5 6 7
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
conservative ondemand userspace powersave performance
1600000
acpi-cpufreq
ondemand
3401000
1600000
<unsupported>
cat: /sys/devices/system/cpu/cpu0/cpufreq/stats: Is a directory
``````
doug@s15:~/temp$ [COLOR=#ff0000]ls -l /sys/devices/system/cpu/cpu0/thermal_throttle[/COLOR]
total 0
-r--r--r-- 1 root root 4096 May 12 23:33 core_power_limit_count
-r--r--r-- 1 root root 4096 May 12 23:33 core_throttle_count
-r--r--r-- 1 root root 4096 May 12 23:33 package_power_limit_count
-r--r--r-- 1 root root 4096 May 12 23:33 package_throttle_count
doug@s15:~/temp$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu0/thermal_throttle/*[/COLOR]
0
0
0
0
``````
doug@s15:~/temp$ [COLOR=#ff0000]ls -l /sys/devices/system/cpu/cpufreq/ondemand[/COLOR]
total 0
-rw-r--r-- 1 root root 4096 May 12 23:36 ignore_nice_load
-rw-r--r-- 1 root root 4096 May 12 23:36 io_is_busy
-rw-r--r-- 1 root root 4096 May 12 23:36 powersave_bias
-rw-r--r-- 1 root root 4096 May 12 23:36 sampling_down_factor
-rw-r--r-- 1 root root 4096 May 12 23:36 sampling_rate
-r--r--r-- 1 root root 4096 May 12 23:36 sampling_rate_min
-rw-r--r-- 1 root root 4096 May 12 23:36 up_threshold
doug@s15:~/temp$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpufreq/ondemand/*[/COLOR]
0
1
0
1
10000
10000
95
```

---

### Post by rigobot on 2013-05-13
Thank you for your response!
I checked every single parameters during a working period and the differences that I found regard:
[LIST]
[*]the frequencies that obviously suite my configuration
[*]the complete absence of the folder "thermal_throttle"
[/LIST]

I can't reproduce any more the malfunctioning...when it will happen again I will update the post.

Thank you anyway.

---

