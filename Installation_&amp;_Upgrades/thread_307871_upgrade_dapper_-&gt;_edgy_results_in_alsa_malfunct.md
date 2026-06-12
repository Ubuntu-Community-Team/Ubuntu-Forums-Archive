---
title: "upgrade dapper -&gt; edgy results in alsa malfunctioning (+solution)"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by phormion on 2006-11-27
Hi, 

I've upgraded from Dapper to Edgy a while ago, and have been encountering problems with multiple programs accessing sound ever since. So far I've solved this problem mostly by rebooting to Windows, but today I decided to dig a bit into it. 

So, the symptoms were that Amarok with XINE and alsa output would not work, only the OSS output; alsaplayer would refuse to play an mp3 (I used the command line from [http://alsa.opensrc.org/index.php?page=DmixPlugin)](http://alsa.opensrc.org/index.php?page=DmixPlugin)), and printing messages like: 

```

ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.ipc_key'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM dmix
snd_pcm_open: No such file or directory (plug:dmix)
Failed to initialize plugin!
Failed to register plugin: /usr/lib/alsaplayer/output/libalsa_out.so
Failed to load output plugin "alsa". Trying defaults.
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.ipc_key'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM dmix
snd_pcm_open: No such file or directory (plug:dmix)
Failed to initialize plugin!
/usr/lib/alsaplayer/output/libalsa_out.so failed to load
NOTE: THIS IS THE NULL PLUGIN.      YOU WILL NOT HEAR SOUND!!

```

It was also causing me problems with Adobe's Flash 9 player beta 2, which worked even worse than beta 1. While posting on the Adobe forums to complain I got the suggestion to try if I have mixing of multiple streams working. 

Since the dmix documentation was pointing me towards ~/.asoundrc, I checked that file and found that it included ~/.asoundrc.asoundconf. I tried commenting out the include statement, and voila! Alsa output works now! 

The contents of my .asoundrc.asoundconf: 

```

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card CA0106
defaults.ctl.card CA0106
defaults.pcm.device 0
defaults.pcm.subdevice -1

```

I have two soundcards in this system, one on-board (Realtek) and one PCI (Audigy 2 SE). The Realtek is disabled from the BIOS, since I suspected it to be faulty, so the only visible sound card to the OS is the Audigy. The module used in snd_ca0106. 

I think this is worth filing as a bug report (there are at least two other occurences of messages like the above ones reported in the forum), since I haven't found anything similar in Malone. I thin the bug is in asoundconf, but I've no idea what's wrong with the above file, since I'm no alsa expert.

Later edit: stupid me, here's the Malone bug against edgy: 

[https://bugs.launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/67998](https://bugs.launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/67998)

Apparently, running asoundconf set-default-card <card> should fix this, too.

---

### Post by angryfirelord on 2006-11-27
Unfortunately, upgrading from distribution to another always results in issues. I just delete the old one and do a fresh install to eliminate any problems.

---

### Post by phormion on 2006-11-27
Unfortunately, some Ubuntu devs have difficulties telling apart 'minor' issues from major annoyances like this one. In the bug report above, somebody notes: 

> 
For Edgy, please add in the release notes that users dist-upgrading from Dapper with an existing ~/.asoundrc.asoundconf will need to manually invoke asoundconf(1) set-default-card [with the correct string appended].


It seems nobody was reading that. Of course, it might be not all users are affected (those with HW mixing, for example, needn't care), but the trouble is, most users can't troubleshoot this. Also, if they use only one music player like Rhythmbox/Amarok, they'll only run into problems when they accidentally need to run two sound streams at a time. 

Anyway, the simple fix could be summarized like this: 

> 
$ asoundconf set-default-card `asoundconf --list | tail -1`


---

### Post by phormion on 2006-12-04
Correction: the above command should be: 

> 
$ asoundconf set-default-card `asoundconf list | grep -v "^Names" | head -1`


And not as as I said in the above post. The option is 'list', not '--list', and the first line from 'asoundconf list' 's output is "Names of available sound cards:", which I filter out.

---

