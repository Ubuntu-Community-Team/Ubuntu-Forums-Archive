---
title: "Fresh install Ubuntu 16.04 codec decode error"
date: 2018-01-15
forum: Installation &amp; Upgrades
---

### Post by aborders on 2018-01-15
I am trying to install Ubuntu 16.04 on a Precision T3600 with a new WD black 1TB hard drive.  I have also tried 17.10 with no luck.  I get to the point where you enter in user information and the install crashes.  I have tried many times with everything google has thrown at me.  Additional note I get the same error when just usbing the live usb version.  Could it be something with the USB drive?

Installing using a live usb.

Here is the end of the crash report.  Any ideas?

[INDENT]PythonArgs: ['/usr/share/ubiquity/install.py']
Traceback:
 Traceback (most recent call last):
   File "/usr/share/ubiquity/install.py", line 754, in <module>
     install = Install()
   File "/usr/share/ubiquity/install.py", line 79, in __init__
     self.generate_blacklist()
   File "/usr/share/ubiquity/install.py", line 227, in generate_blacklist
     for line in manifest_file:
   File "/usr/lib/python3.5/codecs.py", line 321, in decode
     (result, consumed) = self._buffer_decode(data, self.errors, final)
 UnicodeDecodeError: 'utf-8' codec can't decode byte 0xed in position 13: invalid continuation byte
UserGroups: 
_LogindSession: c1
[/INDENT]

---

### Post by aborders on 2018-01-16
I figured it out through trial and error.  It was a bad USB drive.  Not sure why this what not caught and reported sooner.

---

