---
title: "unable to launch software centre"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2011-06-29
If I click on the ubuntu software centre icon the pointer shows the application is loading but then nothing happens

I've done an update, an upgrade and restarted...still nothing

this is both with the linux Mint (gnome desktop) and xubuntu I have installed on this compter an ASUS 13'' P81IJ

....any ideas?

---

### Post by mörgæs on 2011-06-29
Try to reboot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if any.

---

### Post by abelito8 on 2011-06-30
Thank you, I've done it and then launched software-centre through the terminal. Here you have the response

software-center 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 37, in <module>
    from softwarecenter.db.application import Application, DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/application.py", line 31, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 127, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 116, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named LinuxMint

---

### Post by mörgæs on 2011-07-01
I don't know this error message, sorry.

Personally I only use Synaptic for insatlling packages, as it is fast and bug-free as opposed to Software Centre.

---

