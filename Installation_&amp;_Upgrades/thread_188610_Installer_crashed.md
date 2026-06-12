---
title: "Installer crashed"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by yijie on 2006-06-04
Midway during xubuntu installation, the installer throws up an error:


We're sorry; the installer crashed. Please file a bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

---

### Post by FrancoNero on 2006-06-04
my installer also crashed.... around the time it tries to install ide-floppy module

---

### Post by Subbu.exe on 2006-06-04
Err..  I Had Updated Ubuntu since Flight5 till the Final One a Few Days ago..

I Wanted to Give Kubuntu a Shot.. So Downloaded the Desktop CD.
The CD Booted fine.. But When Installing it Gives almost the Same Error as yijie

---

### Post by Jeffala on 2006-07-03
Ditto for me. I too, cannot get Xubuntu to install and I receive errors similar to yijie's post.

However, I have no problem installing Ubuntu or Kubuntu on the same box where Xubuntu fails.

---

### Post by bvsingh on 2006-07-07
i get same error on both xubuntu and ubuntu?
any fix??? i require it urgently!!!

---

### Post by missmoondog on 2006-07-07
same exact problem here just now, trying to install ubuntu 3 times in clean second partiton.

---

### Post by jackubu on 2006-07-11
I'm having also the exactly same problem...

---

