---
title: "Tracing upgrade faults. Unwatchable video playback 18.04"
date: 2019-02-08
forum: Installation &amp; Upgrades
---

### Post by Tadaen_Sylvermane on 2019-02-08
I did an upgrade from 16.04 to 18.04 the other day. Since then my Mythtv playback through Kodi has bit the dust. It runs terrible, the audio is out of sync, the video is jittery. I can confirm that neither Kodi nor Mythtv is the problem as I have a machine PXE booting in the bedroom via LTSP with Kodi that runs mythtv playback just fine. I created the chroot fresh after upgrading so it didn't go through an upgrade process.

How can I test, and or find potential upgrade failures with packages? Dpkg -C is showing me nothing. But something is obviously wrong here that isn't an issue in my LTSP chroot. So far I have purged and reinstalled everything related to Kodi. Kodi packages, xorg, pulseaudio, openbox, lightdm all reinstalled after a purge. Even did an apt clean just to make sure I had fresh downloads.

Both the Chroot and my Host are using Kodi from the ppa, however as said, the bedroom works just fine. It's just the living room that is giving me this issue. I'm lost.

*EDIT* Tried a fresh install on another lvm partition. 18.04 LTS, all new installation. Same exact issue just in the living room :(

---

### Post by Tadaen_Sylvermane on 2019-02-09
Marking as solved, at least for now. The problem still exists however I've narrowed it down to something involving my tv, maybe the hdmi cable or something. I have no issues in my bedroom kodi box or my laptop pulling from this server. Just the living room,which happens to be the server. That rules out Mythtv, Network, failing storage, Kodi being a fresh install rules that out as well.

Only difference left is living room  tv is 4k, others are 1080p.

---

