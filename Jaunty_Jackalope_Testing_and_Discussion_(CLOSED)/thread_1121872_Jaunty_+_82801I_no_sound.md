---
title: "Jaunty + 82801I: no sound"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by logic++ on 2009-04-10
Hi all,
   I installed the 32b Jaunty beta release downloaded today and I get no sound. 
Output:
```
lshw -c multimedia
```
```
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

Any suggestions?
Regards

---

### Post by executorvs on 2009-04-11
I have an acer aspire 6930 and have the same issue. I can get sound from the speakers, but the audio ports and the internal mic do not work.
there seem to be two bug reports on launchpad I think are related.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/329657](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/329657)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/209057](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/209057)
and some discussion on linux laptop wiki at
[http://www.linlap.com/wiki/acer+aspire+6930](http://www.linlap.com/wiki/acer+aspire+6930)

adding the line "options snd-hda-intel model=auto" in /etc/modprobe.d/alsa-base gets the stereo headphone jack working correctly.

the info for Jaunty on the aspire 6930 is as follows:
attached unedited alsa-base file.
ALSA debugging shell script information is located at 
[http://www.alsa-project.org/db/?f=deeadf77f9fdf84a792bb715ac85ded46949ed8a](http://www.alsa-project.org/db/?f=deeadf77f9fdf84a792bb715ac85ded46949ed8a)

  lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

  lsmod | grep snd
snd_hda_intel 435636 3
snd_pcm_oss 46336 0
snd_mixer_oss 22656 1 snd_pcm_oss
snd_pcm 82948 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 10756 0
snd_seq_oss 37760 0
snd_seq_midi 14336 0
snd_rawmidi 29696 1 snd_seq_midi
snd_seq_midi_event 15104 2 snd_seq_oss,snd_seq_midi
snd_seq 56880 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 29704 2 snd_pcm,snd_seq
snd_seq_device 14988 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 62628 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 15200 1 snd
snd_page_alloc 16904 2 snd_hda_intel,snd_pcm

  ps -eaf | grep pulse
USERNAME 3288 3228 0 16:12 ? 00:00:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/USERNAME/.gnupg/gpg-agent-info-USERNAME-laptop /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
USERNAME 3289 3228 0 16:12 ? 00:00:00 /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/USERNAME/.gnupg/gpg-agent-info-USERNAME-laptop /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
USERNAME 3292 1 0 16:12 ? 00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
USERNAME 3298 1 0 16:12 ? 00:00:00 /usr/bin/pulseaudio --start
USERNAME 3299 3298 0 16:12 ? 00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
USERNAME 3717 3593 0 16:17 pts/0 00:00:00 grep pulse

---

### Post by amano on 2009-04-11
[http://ubuntuforums.org/showthread.php?t=1084919&page=9](http://ubuntuforums.org/showthread.php?t=1084919&page=9)

Did you try crimson's test-debs? He called for Intel users to test them out and report back. Nobody answered thus far, thus nobody suffering from problems seems to care to have it fixed.

---

### Post by executorvs on 2009-04-11
I would point out that the audio I do get has none of the pulse volume and crackling issues those test.debs are supposed to be working on.
 
It's more likely a mapping issue when the configs controlling the audio functions are generated. 

As for people troubleshooting the pulse bug, just cuz they aren't all following the same path to a given end doesn't mean people are not working on solving the issue. 
moral: be less judgemental as you don't know all that is being done or people's own reasons for the way they behave.

---

### Post by amano on 2009-04-11
Those patches might fix your problem as well. They are fixing SOME issues, not just an isolated one.

---

### Post by logic++ on 2009-04-12
A bug has already been reported. It has to do with my laptop's model (HP HDX) and I just hope to have it functional on the stable release. Thank you for your time and answers.

Regards

---

