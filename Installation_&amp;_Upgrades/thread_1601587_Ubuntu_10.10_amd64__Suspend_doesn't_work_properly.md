---
title: "Ubuntu 10.10 amd64 : Suspend doesn't work properly"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by mortezamilani on 2010-10-20
I just installed Ubuntu 10.10 amd 64 on HP Pavilion dv5-1299ee. but Suspend functionality doesn't work well.
First I tried to hibernate and with some error messages it worked.
But when I tried to suspend the computer, screen turned off and on two or more times and suddenly login screen appeared. I used Log files to locate where the problem is. I found Nvidia Geforce 9600M GT can't be suspended. so I installed the driver, tried so many things and this line of error took its place to another of AHCI controller. I handled it with using modprobe ahci. and it seems that it worked.
My log shows that there is no problem with suspending devices. but the computer wakes up immediately after suspend.

I really appreciate any help.

 this is the log file ( pm-suspend.log ):

Initial commandline parameters: 
Wed Oct 20 21:07:20 IRST 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux weapi 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_nvhdmi    14587  1 
snd_hda_codec_idt      64667  1 
nvidia              11087157  41 
snd_hda_intel          26019  6 
arc4                    1497  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
iwlagn                202721  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               146875  1 iwlagn
joydev                 11363  0 
tifm_sd                 9780  0 
mac80211              266657  2 iwlagn,iwlcore
snd                    64117  20 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62379  0 
tifm_core               7686  1 tifm_sd
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
hp_accel               13600  0 
jmb38x_ms               8667  0 
psmouse                62080  0 
memstick               10185  1 jmb38x_ms
soundcore               1240  1 snd
serio_raw               4910  0 
lis3lv02d              10352  1 hp_accel
v4l2_compat_ioctl32    12486  1 videodev
lirc_ene0100            7819  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
intel_agp              32080  0 
cfg80211              170293  3 iwlagn,iwlcore,mac80211
lp                     10201  0 
hp_wmi                  6435  0 
parport                37032  3 parport_pc,ppdev,lp
video                  22176  0 
output                  2527  1 video
input_polldev           4527  1 lis3lv02d
lirc_dev               11209  1 lirc_ene0100
firewire_ohci          24679  0 
ahci                   21857  0 
libahci                26167  4 ahci
r8169                  42222  0 
mii                     5261  1 r8169
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  2 hp_accel,sdhci
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
             total       used       free     shared    buffers     cached
Mem:       4056932     590420    3466512          0      23932     191440
-/+ buffers/cache:     375048    3681884
Swap:      1680380          0    1680380

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.110 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Wed Oct 20 21:07:24 IRST 2010: performing suspend
Wed Oct 20 21:07:26 IRST 2010: Awake.
Wed Oct 20 21:07:26 IRST 2010: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa resume suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.3 -> dest=:1.111 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

---

### Post by diazdiego86 on 2010-11-04
Hi! I have this same problem...


I'm thinking I'm gonna try TuxOnIce, but before to do this I want to know if you solve it!

Best regards, Diego!

---

### Post by r0g on 2011-04-16
6 months on and no replies, time to turn this sorry thread around I think!

I've got this problem right now (Apr 2010), can somebody chime in with some troubleshooting steps coz according to the pm-suspend log there's no problem. It just jumps straight from success to awake and hey presto my login screen AGAIN!...

extract...

/etc/pm/sleep.d/action_wpa suspend suspend:success.
Sun Apr 17 04:35:55 BST 2011: performing suspend
Sun Apr 17 04:35:59 BST 2011: Awake.
Sun Apr 17 04:35:59 BST 2011: Running hooks for resume

I don't know what's happening in those 4 seconds but it sure ain't hibernation or suspend (same problem with both). There are no errors in the whole log.

Problem started after moving my drives to a newer faster computer with more memory. I figured I'd need to resize my swap partition to cope with it as I had done previously when I'd upgraded my RAM so...

I changed the mount uuid in fstab and verified it mounts ok. I changed the resume uuid in /etc/initramfs-tools/conf.d/resume to the new swap's uuid. I ran sudo update-initramfs -u which seemed to go fine. I rebooted a bunch of times and still no-dice.

Anyone know how I should proceed?

Might I have to force Ubuntu to re-examine my PC's ACPI/power capabilities? I assumed these were all auto-detected on startup but I'm clutching at straws now :/

Cheers,

Roger.

---

### Post by r0g on 2011-04-17
Okay, the next step it seems is to check /var/log/kern.log

In that 4 second window between suspend/hibernate claiming success and it awakening there was an error that flashed by on the screen too fast to actually read. Turns out this was a message from the kernel telling me the usb3 ports (on my shiny new system) had failed to freeze. This message was however /var/log/kern.log - handy to know next time I get a 1/4 of a seconds worth of error message!

If you have the same problem you can either disable usb3 in your bios, or follow the fixes at the bugtracker entry: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998)

---

