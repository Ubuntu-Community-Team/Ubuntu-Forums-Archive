---
title: "Latest upgrade trashes PC"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2013-12-28
Upgrade the other day trashed my Secretary's PC.  Apprently someone on high decided that my NVidia video drivers weren't any good and put new ones in.    Drivers were NVidia 304.  OS is 12.04 64-bit.  Video will not load in low-resolution mode.  Perhaps those who casued this mess will provide key-stroke by key-stroke instructions for getting my system back.  This system had been a top performer until those in charge on Ubuntu did something bad to one of my systems.

John

---

### Post by steeldriver on 2013-12-28
have a look here, this method seems to have worked for a few people in a similar situation --> [http://askubuntu.com/a/396159/178692](http://askubuntu.com/a/396159/178692)

---

### Post by cigtoxdoc on 2013-12-28
Thank you for your help.  sudo jockey-text did not reveal nvidia drivers.  See below (after fix).  Fix was sudo apt-get update && sudo apt-get upgrade.  This brought up a new version of Grub customizer.  After I installed it, what ever was running put out a whole buch of text dealing with the kernel and inframs.  Lines of code also showed someting about three nvidia drivers (updates, updates-dev, current updates) all referring to 304.108.  When I rebooted after that, it worked.

John

Output of jockey-text was 

holly@john-N68S3B:~$ sudo jockey-text
[sudo] password for holly: 
Additional Drivers
Searching for available drivers...
Exception in thread thread_call_progress_dialog:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Traceback (most recent call last):
  File "/usr/bin/jockey-text", line 128, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 470, in run
    self.backend().shutdown()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
holly@john-N68S3B:~$

---

### Post by grahammechanical on 2013-12-29
If you go to System Settings>Software Sources and untick Proprietary Drivers for Devices (Restricted) then you may not get an update to a proprietary video driver that replaces a working version with a less than satisfactory version.

Have you noticed that the problem seems to be caused by software provided not by Ubuntu developers by Nvidia. I do not use Nvidia drivers because of having problems with their drivers. And another thing. Of course you are frustrated but please do not take it out on us. We are all unpaid volunteers. Besides which no one who uses Ubuntu is a paying customer. Is this not so? That fact limits our right to complain. Would you, as a business person, not agree?

Regards.

---

### Post by cigtoxdoc on 2013-12-29
Thank you for your suggestion.  I have made the change you suggested.  I do not know the how new drivers get in a the update package that is sent out.  Main PCs in my office all have nVidia drivers.  If you need someone to take a look at nVidia drivers that are to be sent out before they goe public, please let me know and I will take a look at them.  It would appear to be much efficient to do this in off-hours before I am not faced with a nonworking machine that my Seretary needs the next business day.

I appreciate the volunteer efforts and would like to be part of the solution.

John

---

