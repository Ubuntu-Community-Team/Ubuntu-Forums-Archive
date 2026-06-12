---
title: "keep lucid-bleed repo?"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by ray field on 2012-01-07
I needed a version of ffmpeg that worked with the latest version of DeVeDe and I couldn't managed to compile it, so a day or two ago I added the lucid-bleed PPA to my sources, and I re-installed mplayer and mencoder, so they might also be from that PPA.  now DeVeDe works, so I'm happy -- however, this morning update-manager came up with a few dozen things it wanted to update.

so I'm not interested in anything bleeding-edge, I deselected [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu) from the Other Sources repos.  do I need to be concerned about anything?  is there a chance something will come along and try to un-update these now-working versions of ffmpeg, mplayer, and mencoder?

---

### Post by dino99 on 2012-01-07
you should not worry. If you are afraid, then lock that ffmpeg package via synaptic

note: bleeding ppa was opened in early Lucid dev time, so long ago. Now newest packages come via "backport" archives into synaptic.

---

