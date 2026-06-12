---
title: "Missing side and top panel in unity"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2013-02-10
I upgraded from Ubuntu 12.04 to Ubuntu 12.10.  Everything is fine up to and including log-in.  After log-in, I can't see the side or top panels on my desktop.  I've tried various suggestions from people with the same problem but no success.

I have a Sony Vaio laptop, model Z590c with a nVidia GeForce 9300 m GS video card.  I don't think I used any nVidia drivers in Ubuntu 12.04 because of some video issues.

Any suggestions please?

---

### Post by papibe on 2013-02-11
Hi raj727.

Open a terminal by pressing Ctrl+Alt+T

Then run:
```
unity --reset
```
Let it run for a few minutes.

Open another terminal and restart your machine:
```
sudo reboot
```
Let us know how it goes.
Regards.

---

### Post by raj727 on 2013-02-11
I got an error message:

WARNING:  no DISPLAY variable set, setting it to :0
ERROR: the reset option is now deprecated

---

### Post by papibe on 2013-02-11
My bad. That option is indeed deprecated.

Try this:
```
sudo add-apt-repository ppa:amith/ubuntutools
sudo apt-get update
sudo apt-get install unity-reset

```
Then:
```
unity-reset
```
Let us know how it goes.
Regards.

---

### Post by raj727 on 2013-02-11
I'm having a problem logging onto my wifi.  I get a message to check my internet connection.  I keep getting disconnected for some reason.  I can't get to the dock which I would use to enter my wifi password.

---

### Post by raj727 on 2013-02-11
I'm asked for an authentication to a network that is not mine.  How would I get to my wifi network?

---

