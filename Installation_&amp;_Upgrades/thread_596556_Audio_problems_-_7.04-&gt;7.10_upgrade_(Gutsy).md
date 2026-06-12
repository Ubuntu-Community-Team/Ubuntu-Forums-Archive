---
title: "Audio problems - 7.04-&gt;7.10 upgrade (Gutsy)"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by delmir on 2007-10-29
Upgraded to 7.10 (Gutsy) caused sound card to no longer be detected.

Mother board: ASUS - M2N-MX with SoundMax HD audio which should use ADI1986A driver or some of the AC9* intel type (I guess). 

It used to work fine on 7.04 after I manually added the follwoing to /etc/modprobe.d/alsa-base:
     options snd-hda-intel position_fix=1 model=3stack

Synaptic shows alsa-base, alsa-oss, and alsa-utils 1.0.14-1ubunt2 installed, but some commands like alsaconf or asoundconf no longer works.

lspci -v shows:
...
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8234
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at dfff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
...

...but...

/etc$ asoundconf list
/etc$ 

...and

/etc$ aplay
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:545: audio open error: No such device
/etc$ 

...and

/etc$ cat /proc/asound/modules
cat: /proc/asound/modules: No such file or directory
/etc$ 

Any help will be appreciated.

Thanks,

Del

PS: I don't want to compile and install alsa from scratch because it's nice to have Ubuntu's auto-updates.

---

### Post by squirage on 2007-10-30
Hi delmir,

  It has been my experience thus far that an OS re-install is in order when your sound card goes missing. I understand that you would prefer to have auto updates of alsa but 14 is old, most people fixed problems with 1.0.15.

  For me sound went bad after a routine update in edgy, thus far most of my issues have appeared to come after unsolicited updates.

My sound help thread for Toshiba satellite users is [http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463)
and it is under Feisty.

A gutsy user who posted to that thread posted a link to this thread [http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374) which she said helped her.

Good Luck.

---

### Post by delmir on 2007-10-31
After 3 days looking around and trying different settings... the following fixed my problem:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
Reboot and setup your sound settings

BTW, m-a re-installed alsa version 14 instead of the newer one 15 and it worked !8-).

---

### Post by igor_birman@yahoo.com on 2007-12-24
It worked, thanks!!  I upgraded from 7.04 to 7.10 and sound didn't work.  Your post was one of the first links I found and it worked right away, thanks!

Igor

---

