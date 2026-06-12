---
title: "[SOLVED] trackerd hogging the cpu"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by cnkbrown on 2007-10-19
This upgrade from feisty to gutsy reminds me why I ditched windows....new unknown processes hogging the cpu... old programs no longer work.... Very frustrating.

sudo apt-get -y purge tracker

then open system monitor and kill the trackerd daemon manually

---

### Post by janarene on 2007-10-20
Thanks cnkbrown.  This utility has no place on my machines and was driving me nuts.

---

### Post by mamadu bwana on 2007-10-21
thanks for the tip.  after trackerd hogged my CPU for over an hour I got really mad and just trashed it. feel better now!

---

### Post by aparigraha on 2007-10-21
XLNT
thx for the tip
worked great

---

### Post by wyth on 2007-10-21
I'd just say after Tracker finishes indexing (which can take some time), it lays right off and stays low.  It's miles more efficient than Beagle in that regard.

---

### Post by fart_flower on 2007-10-23
I have absolutely no need for a desktop search engine and find it a bit odd that something which should be an option was enabled by default.  Easy to install/enable for those that need?  Yes.  Running in the background whether you asked for it or not?  No.  Same goes for the 3D desktop effects.  (Although in the latter case, I absolutely *love* desktop effects.)

At any rate, I did the purge thing as mentioned in this thread.  Thanks.

---

### Post by klepto on 2007-10-24
Thank you soo much! Tracker was running mplayer to see what type of video file I was getting. Using 51% cpu. 

Thanks again!

---

