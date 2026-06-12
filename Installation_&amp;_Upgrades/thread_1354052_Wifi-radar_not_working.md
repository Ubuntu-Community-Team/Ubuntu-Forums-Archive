---
title: "Wifi-radar not working"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by bingobingo on 2009-12-13
After upgrading to 9.10 Wifi-radar stopped working for me. Does anyone else have the same problem? I liked wifi-radar, it was always able to connect when netconnect was more difficult or refuse to connect, and was way easier to use.

This is what I get when I sudo wifi-radar...
 File "/usr/sbin/wifi-radar", line 2915, in <module>
    confFile.read()
  File "/usr/sbin/wifi-radar", line 2798, in read
    self.auto_profile_order = eval(self.get_opt('DEFAULT.auto_profile_order'))
  File "<string>", line 1, in <module>
NameError: name 'linksys' is not defined


It looks like it tried to run but, I do not know what to do next.

---

### Post by darkod on 2009-12-13
Did you try removing it and reinstalling it?
Also, 9.10 might not attach the correct driver to your card.

---

### Post by bingobingo on 2010-02-13
I did what you said, but it did not work.

In Ubuntu 9.10, wifi-radar never worked for me, it is version v2.0.s05-1. Before Ubuntu 9.10 I had no problem using the app.

desktop:/$ sudo wifi-radar
[sudo] password for xxxxxx: 
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 2915, in <module>
    confFile.read()
  File "/usr/sbin/wifi-radar", line 2798, in read
    self.auto_profile_order = eval(self.get_opt('DEFAULT.auto_profile_order'))
  File "<string>", line 1, in <module>
NameError: name 'linksys' is not defined

Looking in /usr/sbin I see that wifi-radar is actually a python script. Is wifi-radar working for anyone else? Dummy me, how do I move this thread to the network/wireless forum?

---

