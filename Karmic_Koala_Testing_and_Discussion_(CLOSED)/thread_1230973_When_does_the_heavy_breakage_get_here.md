---
title: "When does the heavy breakage get here ?"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-08-04
Addmittedly I'm using the Gnome-Core desktop but the Karmic forum seems generally quiet. No major meltdown breakage, just minor annoyances, meanwhile major changes ARE happening. Not complaining, and many kudos to the development team, especially those who consistently join in threads and indulge us, but seriously, where is all the Alpha breakage? Is it just around the corner?

I'd like to use my terminal for more than
```

sudo aptitude update

```
and
```

sudo aptitude safe-upgrade

```

seriously, that is all I've been doing. Put the 190.16 driver against rc5 a few hours ago but other than that i'm totally stable. Even chromium is running beautifully.

---

### Post by kingborel on 2009-08-04
TBH most of the major breakages were back before A1, when the new grub and new GDM came through. There are some persisting problems (PulseAudio) and ongoing issues (suspend/hibernate) but mostly it's been pretty good

---

### Post by autocrosser on 2009-08-04
Yes--the Grub2 conversion broke almost everyones systems--was fun to figure out ;)  The GDM bit was pretty good too....I nuked my main install this last weekend by trying to create a "real" Gnome-Shell session--got a script wrong & b0rked gnome-power-manager fairly bad---Decided to do a clean install--my main had been going from Jaunty Alpha 4 & it was time to re-do it...I just moved to my backup testing install until I get time to do it--next couple of days will do......nice to have four installs to choose from.

---

### Post by caryb on 2009-08-04
For the Kubuntu users KDE 4.3 is being rolled out that should create some havoc.


Cary

---

### Post by Regenweald on 2009-08-04
And that is what is upsetting me, I borked grub2 also, but that was ALL my foolishness. GDM has not provided any problem: I click, i login, done.
As for kde4.3, from all accounts, it seems to be leading to a good release so if grub2 and GDM was all the instability to be expected, I suppose i'll look forward to the new tech coming our way....

Just got upstart 6.3-1, and this:
```

 exaile
INFO    : Loading Exaile 0.2.99.3...
INFO    : Loading settings...
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 56, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 53, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 76, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 102, in __init
    self.__show_splash()
  File "/usr/lib/exaile/xl/main.py", line 221, in __show_splash
    import xlgui
  File "/usr/lib/exaile/xlgui/__init__.py", line 19, in <module>
    from xl import xdg, common, event, metadata, settings, playlist as _xpl
  File "/usr/lib/exaile/xl/playlist.py", line 27, in <module>
    from xl import trackdb, event, xdg, track, collection, settings
  File "/usr/lib/exaile/xl/collection.py", line 244, in <module>
    import pyinotify
  File "/usr/lib/pymodules/python2.6/pyinotify.py", line 104, in <module>
    raise UnsupportedLibcVersionError(LIBC_VERSION)
pyinotify.UnsupportedLibcVersionError: Libc 2.10.1 is unsupported, requires at least Libc 2.4
Exception in thread Thread-2 (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
  File "/usr/lib/python2.6/threading.py", line 730, in run
  File "/usr/lib/python2.6/threading.py", line 378, in set
  File "/usr/lib/python2.6/threading.py", line 289, in notifyAll
<type 'exceptions.TypeError'>: 'NoneType' object is not callable

```
Is the most exciting thing i have going on :) waiting for support for a library. I'm almost brimming over. really i am.

---

### Post by KhaaL on 2009-08-05
you're all a bunch of masochists

---

### Post by nhasian on 2009-08-05
I take it you havent updated the new network-manager-gnome? hehe

> **Regenweald said:**
> ... but seriously, where is all the Alpha breakage? Is it just around the corner?


---

