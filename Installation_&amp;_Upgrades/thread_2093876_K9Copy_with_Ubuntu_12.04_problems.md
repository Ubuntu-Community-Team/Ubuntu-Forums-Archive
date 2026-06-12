---
title: "K9Copy with Ubuntu 12.04 problems"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by bogyman57 on 2012-12-12
Howdy All!

I had K9Copy/VLC/K3b working perfectly on Ubuntu 11.10

BUT when I upgraded <?> to Ubuntu 12.04, K9Copy has a big problem.

I can rip a DVD to an 4400 MB .iso with it just fine (or so it seems)
(other than a new error: "No VTS_TMAPT Available - skipping")

1. VLC crashes when I try to play the .iso file.
(VLC : vm.c 1167 : play_Cell : assertion '0' failed)

2. I can burn the .iso to a DVD+R with K3B and it will play just fine on my stand-alone DVD player.

3. VLC crashes when I try to play that same DVD.

Anybody having the same problems????

---

### Post by bruceliz on 2013-01-08
> **bogyman57 said:**
> when I upgraded <?> to Ubuntu 12.04, K9Copy has a big problem.

I can rip a DVD to an 4400 MB .iso with it just fine (or so it seems)
(other than a new error: "No VTS_TMAPT Available - skipping")

1. VLC crashes when I try to play the .iso file.
(VLC : vm.c 1167 : play_Cell : assertion '0' failed)

2. I can burn the .iso to a DVD+R with K3B and it will play just fine on my stand-alone DVD player.

3. VLC crashes when I try to play that same DVD.

Anybody having the same problems????

Exactly, or almost. I have no stand-alone DVD player, and I'm running 12.10, but otherwise my experience is identical. 

K9Copy creates ISOs, vlc can play individual video files from the (mounted) ISO, but it (and totem, and mplayer) crash immediately when used to open the ISO file for playing, though they play ISOs created in earlier releases of Ubuntu without difficulty.

Hopefully temporary workaround: DVD Shrink installed in ~/.wine ...

---

