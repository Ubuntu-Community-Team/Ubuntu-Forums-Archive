---
title: "No Sound and Firefox Hanging"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by petermck on 2011-10-23
When searching for problems related to sound and Firefox running slow or other issues like this, I came up with so many posts that I decided to start a new one because this fix seems to have worked on various problems.
After a fresh install of 11.10 64-bit, I had various problems:
[LIST]
[*]Firefox hanging for a long time when trying to right click and open a link in a tab or new window
[*]Firefox not playing video in Youtube
[*]Firefox generally operating slowly
[*]No sound
[*]Other applications/Firefox extns (possibly related to sound??) seemed to hang sometimes.
[/LIST]
On the advice of another post at [http://ubuntuforums.org/showthread.p...hlight=banshee]("http://ubuntuforums.org/showthread.p...hlight=banshee") I did this:
```
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
```
When removing alsa-base, apt-get also removed some ubuntu-desktop associated stuff so I also:
```
sudo apt-get install ubuntu-desktop
```
and then rebooted. I suggest it's fairly important (or at least prudent) to do the sudo apt-get install ubuntu-desktop step before rebooting. I'm not sure what affect omitting this might have.

As far as I can tell, everything seems to be working properly now. The only remaining issue I see is that the speaker icon has disappeared from the toolbar, but this is minor.
All the other issues listed above seem to have been fixed.

---

### Post by ReFranz on 2011-10-24
Problem here, also w/ 64 bit, is that the sound is too loud, dangerously loud. Do you know FOR SURE if this fix will work for the LOUD problem?

---

### Post by petermck on 2011-10-29
> **ReFranz said:**
> Problem here, also w/ 64 bit, is that the sound is too loud, dangerously loud. Do you know FOR SURE if this fix will work for the LOUD problem?

No I don't, but my sound has no problems with the volume.

---

