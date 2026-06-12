---
title: "Lubuntu 12.04 Installation quitting"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by adam_d on 2012-05-04
Hi guys,

I'm having a problem during install of Lubuntu 12.04 on an IBM Thinkpad A21p. Quick Specs are:

P3 850mhz
512mb Ram
32gb Hard Drive
ATI Rage Mobility 128

During install, either by loading to the live desktop first, or just going directly to the installer, I get about, 20% through, at the copying files stage, and the installer just quits on me. In /var/log/syslog I see this.

```
May  4 19:58:56 lubuntu install.py: Exception during installation:
May  4 19:58:56 lubuntu install.py: Traceback (most recent call last):
May  4 19:58:56 lubuntu install.py:   File "/usr/share/ubiquity/install.py", line 689, in <module>
May  4 19:58:56 lubuntu install.py:     install.run()
May  4 19:58:56 lubuntu install.py:   File "/usr/share/ubiquity/install.py", line 129, in run
May  4 19:58:56 lubuntu install.py:     self.copy_all()
May  4 19:58:56 lubuntu install.py:   File "/usr/share/ubiquity/install.py", line 465, in copy_all
May  4 19:58:56 lubuntu install.py:     self.db.progress('SET', 10 + copy_progress)
May  4 19:58:56 lubuntu install.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 60, in <lambda>
May  4 19:58:56 lubuntu install.py:     lambda *args, **kw: self.command(command, *args, **kw))
May  4 19:58:56 lubuntu install.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 81, in command
May  4 19:58:56 lubuntu install.py:     status = int(status)
May  4 19:58:56 lubuntu install.py: ValueError: invalid literal for int() with base 10: ''
May  4 19:58:56 lubuntu install.py: 
```

Then I get dumped back to the desktop, and the mouse cursor jams on the spinning loading cursor. If I try to reboot from the hard drive, it does something, then just sits at a blinking cursor.

The disc tests OK, and I have tested it using VirtualBox where it installed fine. Does anyone have any ideas? Any help is much appreciated.

---

### Post by adam_d on 2012-05-05
Sorry for the bump, but does anyone have any suggestions?

I managed to find this, which also seems to be the same problem, but does seem to be isolated as it only seems to affect one other person. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/985354](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/985354)

---

### Post by adam_d on 2012-05-05
Sorry for bumping again, but it's just to say I sorted this one using the alternate CD, so I guess it's definitely a bug in ubiquity.

---

