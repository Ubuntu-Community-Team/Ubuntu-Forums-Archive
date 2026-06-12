---
title: "hibernate hangs after upgrade to 9.10"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by jeanlucmalet on 2009-12-11
Hi!
I'm new ubuntu user, I've installed 9.04, all was working fine, hibernate and suspend
then I upgraded to 9.10, since then I can't hibernate the laptop anymore

the symptoms are :
start to hibernate
the screen become dark
disk activity (probably memory dump)
then nothing.... no activity, no error message, I've to stop the laptop by pressing power button during 5s
I've tested to wait 30min, same result

the laptop is a dell latitude e6400
in the log I got :
Initial commandline parameters: 
Sat Nov 28 09:03:27 CET 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux maletjl-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  4 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
arc4                    1660  2 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
ecb                     2524  2 
snd_rawmidi            22208  1 snd_seq_midi
iwlagn                109052  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mmc_block              10592  2 
joydev                 10272  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlcore               112508  1 iwlagn
snd_timer              22276  2 snd_pcm,snd_seq
mac80211              181236  2 iwlagn,iwlcore
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 36808  0 
snd                    59204  21 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
psmouse                56500  0 
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  2 iwlcore,sdhci
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211               93052  3 iwlagn,iwlcore,mac80211
serio_raw               5280  0 
iptable_filter          3100  0 
dell_wmi                2564  0 
ricoh_mmc               3676  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
lp                      8964  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
usbhid                 38208  0 
ieee1394               86596  1 ohci1394
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
e1000e                122124  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
             total       used       free     shared    buffers     cached
Mem:        978312     938764      39548          0     138364     236764
-/+ buffers/cache:     563636     414676
Swap:      1060280     492388     567892
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Sat Nov 28 09:03:30 CET 2009: performing suspend

any idea?

---

### Post by lemming465 on 2009-12-12
If you have (or are willing to set up) a launchpad account, report it as a bug.  Probably against your kernel package ("linux-image").  If you are feeling adventurous, you could try a live daily-build CD from the future Lucid Lynx line of development, and see if that can suspend and resume.  If not, definitely report a bug.  If Lucid can suspend and resume OK, you could try running a newer kernel with Karmic.

---

### Post by jeanlucmalet on 2010-01-08
after some update, it's now working well almost.

suspend to ram is working fine

suspend to disk don't hang anymore, it does dump the ram (lot of disk activity) then power off the laptop :popcorn:

but when resume time comes.... well it don't! it start as if resuming.... then end by a normal boot... looking to the 8th console (seems that some log are outputed there) I saw a message like "found a software suspend swap signature, rewriting swap signature" ....
since it had found a software suspend swap signature, why didn't it resumed it?
thanks and regards
JLM

---

### Post by lemming465 on 2010-01-08
Beats me why it isn't resuming.  One question: is the regular shutdown and boot fast enough for your purposes?  If so, you could ignore hibernate/resume.

If resume is flaking out, it might be worth trying to erase and reformat the swap space.  Are there any other Linux OS's using the same hard drive?  They will tend to try to use all the same swaps.  If any are heavily into encryption, they will want to encrypt the swap partition too.

Assuming you are using a single swap partition, say sda5, you could do something like this:```
sudo -i
swapoff -a
dd if=/dev/zero of=/dev/sda5
mkswap /dev/sda5
```
Make sure that you don't wipe out any disk partitions that _aren't_ swap; this *will* destroy data if you get it wrong.

Check /etc/fstab and if necessary change the swap target (first field) from UUID to partition (e.g. /dev/sda5).  Or run *blkid* and paste in the new value.  Once fstab agrees with the disk again, you can do *sudo swapon -a* to resume swapping, and then see if hibernate & resume works any better.  Maybe yes, maybe no.

---

### Post by jeanlucmalet on 2010-01-11
thanks for the response. Sadely it didn't helped, I still have the same issue after re-creating the swap...

---

