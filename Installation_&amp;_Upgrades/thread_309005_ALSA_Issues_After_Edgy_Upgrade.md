---
title: "ALSA Issues After Edgy Upgrade"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by Jivicin on 2006-11-29
I had ALSA working flawlessly in Dapper.  I could hear multiple sounds at once and all was well.  I've been using Edgy for awhile now and am only able to have one sound at a time playing.  I believe it has something to do with the aplay command in the console:

```
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.ipc_key'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM dmix
aplay: main:547: audio open error: No such file or directory

```

Thoughts?

EDIT:  Solved.  my ~/.asoundrc got overwritten with the update.  There was a backup made that had the correct settings.  This solved the problem.

---

