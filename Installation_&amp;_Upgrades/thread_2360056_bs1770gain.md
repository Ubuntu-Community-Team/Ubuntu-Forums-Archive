---
title: "bs1770gain"
date: 2017-05-01
forum: Installation &amp; Upgrades
---

### Post by jwn-2 on 2017-05-01
Ubuntu 14.04 LTS

I had bs1770gain installed on my old computer and it was working perfectly fine. However on my new computer I get “E: Unable to locate package bs1770gain” when I run sudo apt-get install bs1770gain. I vaguely remember that I had to set a software source or something somewhere, but I can’t remember what or where and I can’t find it again on the web. Can anyone please help? I don’t have the old computer any more to check.

---

### Post by oldos2er on 2017-05-01
It doesn't appear to be available for Trusty 14.04: [http://packages.ubuntu.com/search?keywords=bs1770gain](http://packages.ubuntu.com/search?keywords=bs1770gain)

---

### Post by ajgreeny on 2017-05-01
I can not find anything but source code which you will have to build yourself, but as an alternative you could also look at **mp3gain** from a ppa at [https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio](https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio) which, from what I read about bs1770gain, looks as if it does the same thing. I have used mp3gain quite a lot in the past when converting old vinyl LP records, via recordable audio CDs, to digital mp3 files.

You could also consider easymp3gain which is in the standard 16.04 repos, but which I have never tried; this adds a GUI (either gtk or qt depending on which you choose), and you may prefer to do things that way.

The addition of mp3splt and mp3wrap may also be very useful; mp3splt will split mp3 files into parts in several different modes and does it in a lossless manner without decoding and re-encoding, and mp3wrap will join mp3 files together, again without loss.

---

