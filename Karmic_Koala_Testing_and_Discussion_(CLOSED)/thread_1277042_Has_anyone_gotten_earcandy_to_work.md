---
title: "Has anyone gotten earcandy to work?"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ninjapirate89 on 2009-09-27
[http://d0od.blogspot.com/2009/09/fade-music-skype.html](http://d0od.blogspot.com/2009/09/fade-music-skype.html)

I added the PPA and installed it, but it doesn't want to work for me.

---

### Post by Eestlane on 2009-09-27
Tried this?
[http://d0od.blogspot.com/2009/09/fade-music-skype.html#comment-17636620](http://d0od.blogspot.com/2009/09/fade-music-skype.html#comment-17636620)

---

### Post by KillerKiwi on 2009-09-27
Ear candy has not been tested on karmic yet... mostly due to my third child interrupting any free time :)

That being said it should work if you turn flat volume off

I've also been *slowly* working on a rewrite at
[https://code.launchpad.net/~killerkiwi2005/earcandy/0.7](https://code.launchpad.net/~killerkiwi2005/earcandy/0.7)

It should be more stable and will allow multiple output devices to be controlled (ie always put music out my speakers but phone to my head phones).

---

### Post by ninjapirate89 on 2009-09-27
I just installed Karmic on my laptop today and I'm already doing a reinstall (I'm not to patient with fixing things :P). My sound quit working (not sure if earcandy caused it) and I did something to cause it to stop booting correctly (I think its because I shutdown while startupmanager was saving changes). In any case, I think I'll wait until earcandy is more developed before I try it again. I can't wait until it's fully functional. It seems like an awesome program.

---

### Post by bluebyt on 2009-09-28
I get this error on karmic:

```
Traceback (most recent call last):
  File "/usr/bin/earcandy", line 17, in <module>
    import ear_candy
  File "/usr/share/earcandy/ear_candy/ear_candy.py", line 20, in <module>
    import wnck
ImportError: No module named wnck
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 100, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 13] Permission denied: '/var/crash/_usr_share_earcandy_ear_candy_ear_candy.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/earcandy", line 17, in <module>
    import ear_candy
  File "/usr/share/earcandy/ear_candy/ear_candy.py", line 20, in <module>
    import wnck
ImportError: No module named wnck

```

---

### Post by KillerKiwi on 2009-09-29
> **bluebyt said:**
> I get this error on karmic:

```
Traceback (most recent call last):
  File "/usr/bin/earcandy", line 17, in <module>
    import ear_candy
  File "/usr/share/earcandy/ear_candy/ear_candy.py", line 20, in <module>
    import wnck
ImportError: No module named wnck
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 100, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 13] Permission denied: '/var/crash/_usr_share_earcandy_ear_candy_ear_candy.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/earcandy", line 17, in <module>
    import ear_candy
  File "/usr/share/earcandy/ear_candy/ear_candy.py", line 20, in <module>
    import wnck
ImportError: No module named wnck

```

install [python-gnome2-desktop]("apt:python-gnome2-desktop")

---

### Post by LKjell on 2009-09-30
There is a module that cork music on phone, when somebody is calling in Skype Totem music gets muted. Unfortunately there is a bug and the music gets muted indefinitely.

---

### Post by bluebyt on 2009-09-30
> **KillerKiwi said:**
> install [python-gnome2-desktop]("apt:python-gnome2-desktop")
Thanks work great!

---

