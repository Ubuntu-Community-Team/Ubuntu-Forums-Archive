---
title: "sound in some applications, not in others, 7.10"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by shochh on 2007-10-24
Hi all.
I upgraded to 7.10 from 7.04, but after the upgrade my system had no sound. I searched the forums, read through the Comprehensive Sound Guides, but still no luck. However, for some reason I opened Totem to play a DVD and found that the sound in Totem worked.

I am using a Diamond Extreme Sound Card with PC speakers. So far Totem is the only application that has been able to play sound- I've tried Amarok, Firefox, Pidgin, but got nothing, and also no system sounds work.

Here's what I've tried so far:
alsamixer; checked that nothing was muted
aplay -l; the system recognized the sound cards both on the mobo and the sound card
asoundconf set-default-card <card name>
purging and reinstalling the alsa drivers

Does anyone have any ideas on what else I should try? I'm hoping to avoid doing a complete install of Gutsy, but will do it if nothing else seems possible.

---

### Post by fearevilleet on 2007-10-24
Hi,

I am having the same issue. My sound card was not working or even seen by ubuntu. I had to reinstall drivers which fixed the issue. I was trying to get sound to come out of vlc for 45 minutes, I tried mplayer and it worked fine...... go figure. 

Let me know if you find a solution for this issue, boy to I wish I stuck with edgy.

---

### Post by ztirffritz on 2007-10-25
During the upgrade there was a window that said to do something with ALSA, but I didn't have access to the CLI during the upgrade so I couldn't do what it was asking.  Now I can't remember what it was asking me to do.  At any rate, I have no sound now.

---

### Post by shochh on 2007-10-25
The message I got said to do: "asoundconf set-default-card <card name>". I tried it, but no luck.

---

### Post by shochh on 2007-10-29
Ok, doing a complete install from a cd fixed the problem. Not sure what the issue was, but will probably just install new versions from scratch next time instead of upgrading. Bit of a bummer, but definitely not worth dropping ubuntu over.

---

