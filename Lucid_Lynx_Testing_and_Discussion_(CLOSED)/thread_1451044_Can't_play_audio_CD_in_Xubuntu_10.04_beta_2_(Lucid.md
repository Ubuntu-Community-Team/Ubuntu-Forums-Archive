---
title: "Can't play audio CD in Xubuntu 10.04 beta 2 (Lucid)"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brunogirin on 2010-04-09
Hi all,

I just installed Xubuntu 10.04 beta 2, updated all packages through apt-get dist-upgrade to make sure everything was up to date and I am unable to play audio CDs. The symptoms are:

1. insert an audio CD in the drive
2. try to play it with Exaile
=> Exaile sees the CD and is able to give me a list of tracks but can't play any of them
3. try to play it with Rhythmbox or Listen
=> Neither of those actually show the CD

I had Xubuntu 9.10 (Karmic) installed on that same machine for a few hours earlier today and it worked well with Karmic so I am reasonably sure that it's not a hardware problem. The fact that none of the 3 music players mentioned above manage to play the CD suggests that the issue is not with the music player itself.

Has anybody got any idea as to where I should look to start debugging that problem? Could it be an issue with gstreamer? Am I missing a specific codec? Are there any logs I can search?

Also note that I installed Ubuntu Restricted Extras in order to have Flash and a few other things.

Cheers,

Bruno

---

### Post by bichopro on 2010-04-09
try remove ubuntu-restricted-extras and install xubuntu-restricted-extras

---

### Post by brunogirin on 2010-04-09
Nope, no difference at all. I have the feeling that both ubuntu-restricted-extras and xubuntu-restricted-extras are just meta-packages that depend on a lot of other packages and that the xubuntu version doesn't install anything more than the ubuntu one.

---

### Post by lidex on 2010-04-11
Could well be gstreamer.
Have a look here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by brunogirin on 2010-04-11
@lidex: yes I thought about that so I installed the gstreamer command line tools and the following works as expected:

```
gst-launch cdiocddasrc ! pulsesink
```

I even managed to create a small python program that plays the CD via gstreamer. Or maybe it could be an issue with a part of gstreamer that my short program doesn't use but that all the real music players do use. I'll get the Exaile sources and see if the latest version solves this and if not try to narrow it down to the exact point where it fails.

---

### Post by trig on 2010-04-11
Im still learning code so can someone tell me what cdiocddasrc means?

---

### Post by overdrank on 2010-04-11
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by brunogirin on 2010-04-11
@trig: cdiocddasrc is a source plugin available with gstreamer to read from an audio CD. Bascially, the way gstreamer works, you create an audio/video pipeline from a source to a sink. So what the command above does is start the cdiocddasrc source, which reads from audio CD and pipes it to the pulsesink sink, which sends the audio to pulseaudio.

You can find more details about all this here: [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

---

### Post by lidex on 2010-04-11
Exaile PPA:
[https://launchpad.net/~exaile-devel/+archive/ppa]("https://launchpad.net/~exaile-devel/+archive/ppa")

I'm using this version^

---

### Post by brunogirin on 2010-04-11
Thanks lidex!

---

