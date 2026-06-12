---
title: "Attempted to install new display drivers and can no longer boot, help!"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by daltonlaffs on 2008-09-28
Hello forum peoples,

A few days ago, I needed an update to my Nvidia drivers (restricted) because I was noticing glitches and was hoping a more recent version would have them fixed.

I forgot that I could probably do said updating with the package manager and went straight to the Nvidia website. They had 32-bit Linux drivers, so I downloaded it. I tried to run it in Terminal, but it said that I needed to shut down my X server. Fair enough.

Since taking out the GNOME manager wouldn't return me to a root prompt, I went back into terminal and ran "sudo init 1". That dropped me to a root pretty well, so I cd'd to the file and ran it.

It warned me that I shouldn't run it from state 1, but I was thinking at that point "What's the worst thing that can happen?!" and installed it anyway. Then I rebooted, and Ubuntu froze on a black screen after the progress bar.

What can I do? I think I screwed myself. I have a system backup from a week before and can copy across any file you think will help me. I've already replaced my xorg.conf with a backup, and the problem is persisting.

Kudos to the dude who figures this out for me!

---

