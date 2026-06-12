---
title: "VLC: All components will not install"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2010-07-30
Hello,

I am helping some friends.

I tried installing VLC through Synaptic. However, i got the reply "all components could not be installed". VLC does not appear in the menus. All four software repositories have been ticked.

How can I install VLC?

Thanks

---

### Post by drpjkurian on 2010-07-30
Hi
Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have an universe repository activated.
Search for vlc and install it. You should install vlc-plugin-pulse/ and mozilla-plugin-vlc as well.
If you are interested in streaming or transcoding, you should additionnally install libavcodec-extra-52 from a multiverse repository.

---

### Post by yc2 on 2010-07-30
Thanks drpjkurian,

Good advice, but main problem still not solved,

main, restricted, universe, multiverse  all marked

---

### Post by dino99 on 2010-07-30
you might have some packages conflicts, are you using ppa, which distro and vlc release are you talking about ?

you might not have issue with the genuine ubuntu repo

---

### Post by yc2 on 2010-07-30
Thanks dino99,

They use Lucid with an almost identical (very simple) setup as I do.

No "special" changes of the repositories. Just checking main, restricted, universe, multiverse. All standard. No ppa:s.

The repositories are from ubuntu standard servers that were set up default during an installation in Sweden.

EDIT: I think you have a good idea there dino99. Next time I go to these friends I will try another standard Ubuntu server from another country or district in Sweden, or Ubuntu main server.

Sorry I can't see which version of VLC. Synaptic was recently updated so i assume it is the "current" version.

---

