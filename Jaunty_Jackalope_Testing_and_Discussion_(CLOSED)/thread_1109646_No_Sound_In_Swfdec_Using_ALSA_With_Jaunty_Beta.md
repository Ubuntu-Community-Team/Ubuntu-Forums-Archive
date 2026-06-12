---
title: "No Sound In Swfdec Using ALSA With Jaunty Beta"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-03-29
So many prepositional phrases! Whew!

The title speaks for itself. The video is GREAT, flawless, but the sound  (e.g., on YouTube) isn't working. I use ALSA on HDA Intel, and would rather not use PulseAudio as it's pretty awful for me.

Any insights?

Thanks!

---

### Post by iaskedalice09 on 2009-03-29
Just tried Pulseaudio - no luck.

---

### Post by iaskedalice09 on 2009-04-03
BUMP
Response, please?

---

### Post by Zorael on 2009-04-04
Not sure it's related, but when I couldn't get Flash to play when everything else worked, it was because it factored in a channel I had muted.

I have Master, Headphone, PCM and Front channels, that all affect sound output multiplicatively. Every other app just take Master, Headphone and Front into consideration, while Flash for some reason wants PCM as well. Which was muted.

So, check yon alsamixer.

---

### Post by ubu-for on 2009-04-04
Try version 0.9.2 from the [PPA repository]('https://launchpad.net/~swfdec-team/+archive/ppa').

---

### Post by iaskedalice09 on 2009-04-10
Went with the repos fix and got this error in Terminal:

```

W: Duplicate sources.list entry http://ppa.launchpad.net jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_swfdec-team_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

How to fix this? Thanks.

---

### Post by iaskedalice09 on 2009-04-10
Ran sudo apt-get clean and sudo apt-get check and it is solved. Updating now then restarting. I didn't see swfdec on the updates list OR withheld packages, so I assume I have the wrong repos. I'll let you know after the reboot.

---

### Post by iaskedalice09 on 2009-04-10
No luck. I'm trying to install 0.9.2 from a binary now. I'll let you know.

---

### Post by iaskedalice09 on 2009-04-10
OK, if you have no sound on gnash or swfdec with YouTube run the following command and it should work

```

sudo apt-get install libgstreamer-plugins-base0.10-dev

```

It says it's now using gnash even though the unstable swfdec installed just fine...I can't find the plugin file but I don't care! I HAVE SOUND!

---

