---
title: "Echo Gina soundcard trouble"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by nsj on 2006-03-04
Hello all,

I have an nforce2 motherboard with onboard sound and that worked fine.  But I also have a (nice) Echo Gina soundcard in my PC and wanted to get that to work.  I followed some guide on-line, which seems to have stopped my nVidia onboard audio working, and also not had the desired effect of getting the Echo card to work.

Here's the output of *lsmod|grep gina*:
[INDENT]
snd_gina20             26404  0
firmware_class         10240  1 snd_gina20
snd_pcm                91528  2 snd_gina20,snd_pcm_oss
snd                    59108  5 snd_gina20,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd _timer
snd_page_alloc         10952  2 snd_gina20,snd_pcm[/INDENT]

Does anybody know how I might get it working from here? The modules all seem to be loaded (don't they?), but Ubuntu doesn't want to show them in Preferences\Multimedia Systems Selector or Preferences\Sound.  Does anybody kno what might be going wrong/how I might get the Echo card working?

And is there a quick fix to get the nVidia card working again? I really need sound!

I'm much obliged to you all.

thanks,
nsj.

(I've just noticed this is in kind of the wrong place, but I can't seem to be able to delete and repost appropriately. Could a mod help me out on this, please?)

---

