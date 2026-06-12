---
title: "Breezy to Dapper upgrade problem"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by gray380 on 2006-06-16
Hi there

After updating the distribution (5.10 to 6.06 via update manager) there were following problems:

- sound was gone

$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

$ ls -l /dev/dsp
lrwxrwxrwx 1 root root 4 2005-12-26 18:57 /dev/dsp -> dsp0

- problem with package installing/updating vis synaptic (I did not change any adjustments)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-tools/alsa-tools_1.0.10-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-tools/alsa-tools_1.0.10-1ubuntu1_i386.deb)
  407 Proxy Authentication Required

Any assistance?

brg,
Serhiy.

---

### Post by gray380 on 2006-06-16
Hi there

I have solved a problem, but somehow through an *** (dupu):

```
$ sudo -s
# export http_proxy="http://DOM\NAME:PASSWD@proxy.com:9090/"
# export https_proxy="http://DOM\NAME:PASSWD@proxy.com:9090/"
# apt-get update
# apt-get dist-upgrade

```

In the Breezy all was good, when will correct mistakes in the current (Dapper) distribution?

brg,
Serhiy.

PS I shall repeat,   proxy-configuration in system did not changed.

---

### Post by gray380 on 2006-06-16
Hi All

I solved the problem with apt-get by adding the following strings to the /etc/environment:

```
https_proxy="http://Domain\Name:passwd@proxy.server.com:9090/"
http_proxy="http://Domain\Name:passwd@proxy.server.com:9090/"
ftp_proxy="http://Domain\Name:passwd@proxy.server.com:9090/"
```

That I have noticed with a sound, before updating there were following values:

**$ lsmod |grep snd**
snd_intel8x0 30144 1
snd_ac97_codec 72188 1 snd_intel8x0
snd_pcm_oss 46368 0
snd_mixer_oss 16128 2 snd_pcm_oss
snd_pcm 78344 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 21764 1 snd_pcm
snd 48644 6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_timer
soundcore 9184 2 snd
snd_page_alloc 10120 2 snd_intel8x0,snd_pcm

after updating:
**$ lsmod|grep snd**
snd_mixer_oss          19296  0
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  1 snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  6 snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

before:

**$ cat /proc/asound/oss/sndstat**
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux Cherpatyuk 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Intel 82801DB-ICH4 with AD1981B at 0xd0100c00, irq 10

Audio devices:
0: Intel 82801DB-ICH4 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1981B

after:
**$ cat /proc/asound/oss/sndstat**
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux Cherpatyuk 2.6.12-10-686 #1 Fri Apr 28 13:21:56 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG

Why???

brg,
Serhiy.

---

