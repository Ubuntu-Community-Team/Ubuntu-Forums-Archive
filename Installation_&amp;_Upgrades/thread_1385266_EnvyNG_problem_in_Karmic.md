---
title: "EnvyNG problem in Karmic"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by bferd on 2010-01-19
Hi. I'm having a problem running EnvyNG. Nothing happens when I start from the lancher and in text mode I get this error:

> brad@bjs:~$ envyng -t
Traceback (most recent call last):
  File "interface.py", line 428, in <module>
    a = Interface()
  File "interface.py", line 126, in __init__
    self.abstract = abstraction.Abstraction(progress, True)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 35, in __init__
    self.hardware = detection.HardwareDetection()
  File "/usr/lib/python2.6/dist-packages/Envy/detection.py", line 48, in __init__
    self.getCards()
  File "/usr/lib/python2.6/dist-packages/Envy/detection.py", line 144, in getCards
    self.atiOrderedList = self.drivers['fglrx'].keys()
KeyError: 'fglrx'


I've tried
$ sudo apt-get --purge remove envyng-qt
$ sudo apt-get install envyng-qt
$ envyng -t

Checked bug report for solution  [_[COLOR="Blue"]here[/COLOR]_]("http://bugs.launchpad.net/ubuntu/+source/envyng-qt/+bug/501776")

---

### Post by bferd on 2010-01-19
Any ideas? Help please.

---

### Post by darkod on 2010-01-19
I have no idea, but you can also try removing envyng-core, not just envyng-qt. Something like:

sudo apt-get remove --purge envyng-core envyng-qt
sudo apt-get install envyng-core envyng-qt

---

### Post by Elcid247 on 2010-04-01
i got same thing here, any1 found a solution yet?

---

### Post by Krovas on 2010-04-17
Ditto. Envy was a slick way to install Nvidia drivers.

---

