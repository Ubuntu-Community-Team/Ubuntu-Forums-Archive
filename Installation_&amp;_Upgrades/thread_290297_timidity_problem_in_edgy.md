---
title: "timidity problem in edgy"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by nalle on 2006-11-01
Hello

After upgrading to edgy I have a problem with timidity. Before it worked, but now it returns an error when starting or stopping and because of it I can't either remove or configure it again.

here is the error from a dpkg reconfigure:

> 
 * Stopping TiMidity++ ALSA midi emulation...                                     [fail] 
invoke-rc.d: initscript timidity, action "stop" failed.
dpkg: error processing timidity (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting TiMidity++ ALSA midi emulation...                                            ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
invoke-rc.d: initscript timidity, action "start" failed.



my sounds work fine otherwise. I'm using an ALSA mixer.
Can anyone tell me what to do?

-nalle

---

### Post by engine on 2007-09-23
Same problem trying to update to 7.04 - the update doesn't like timidity, to the point of refusing to update anything, and synaptic fails to remove timidity:
```
subprocess pre-removal script returned error exit status 1
```
Both nalle and I would appreciate some advice and support here!
Thanks in advance.

---

### Post by engine on 2007-09-23
How I hate it when "a system" cannot get its own components understanding what's going on. All I can report is that after the upgrade to 7.04 assured me it had failed, it now seems to have succeeded. And now I've managed to use synaptic to remove timidity.

---

