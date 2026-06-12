---
title: "Firefox lucid lock-up"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by max1e6 on 2010-06-24
Recently upgraded Karmic to Lucid (32 bit system)

System freezes/locks-up intermittently (seems to be associated with Firefox). Only option is to power off.

Have seen other (very recent) posts, many unanswered and none of use.

Any ideas?

---

### Post by arrange on 2010-06-24
Have you had a system lock-up _without_ FF running? What if you use a different browser for a test?

---

### Post by max1e6 on 2010-06-24
On the first couple of lock-ups I didn't make a note of what I was running (primarily because I suspected a hardware issue), but in all of the lock-ups since, yes, I have been running FX.

I can run Opera with no problems. Some of the sites I go to (Rhapsody) are not compatible with Opera so I must use FX.

---

### Post by arrange on 2010-06-24
Do you see any messages in */var/log/syslog* or */var/log/syslog.1* around the time a lock-up happened?

---

### Post by max1e6 on 2010-06-25
Have a test session with the freeze. Mostly unintelligible to me. Is it safe to post it here?

Thanks

---

### Post by arrange on 2010-06-25
If it doesn't contain a virus :)
I think you can post it here (use the CODE tags), or if it's too long, use [Ubuntu pastebin]("http://paste.ubuntu.com/").

---

### Post by max1e6 on 2010-06-25
OK, I'm new to this pastebin tool, but here goes:[http://paste.ubuntu.com/455105/plain/]("http://paste.ubuntu.com/455105/plain/")

---

### Post by arrange on 2010-06-25
Can you check if the lock-up is connected with playing sound/video within the browser?

---

### Post by max1e6 on 2010-06-25
I use the FX browser almost exclusively for audio.

Thanks

---

### Post by arrange on 2010-06-25
Looks like it is this bug
[http://www.linux-archive.org/debian-kernel/390110-bug-586967-bug-scheduling-while-atomic-irq-11-b43-2018-0x00000101.html](http://www.linux-archive.org/debian-kernel/390110-bug-586967-bug-scheduling-while-atomic-irq-11-b43-2018-0x00000101.html)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/533335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/533335)

It's not connected with sound, but wifi.

---

### Post by max1e6 on 2010-06-25
Ok, so the fix would go something like this?

sudo modprobe -r 3c59r



If I do this, do I run the risk of being locked out on reboot?

---

### Post by arrange on 2010-06-25
I don't use wifi, so I don't know.
But generally this command is temporary, on reboot you will be where you were before. Or you can use```
sudo modprobe 3c59r
```to get the module loaded again.

---

### Post by max1e6 on 2010-06-25
With Ubuntu, my mp3 service (Rhapsody) seems to only work with Firefox and the shty Adobe plug-in. I'm not sure why my set-up wants to use wifi instead of sound. Like one of the poor fellows in the bug links you provided, I have this installation on an antique Dell (Inspiron 8200). I wonder if I have a Firefox/Adobe configuration problem or a machine configuration problem... Just today I had a freeze-up occur while recording a record with Audacity. This time, FX wasn't running.


It looks like one of the users in the bugs links solved his problem by unloading module 3c59r. (sudo modprobe -r 3c59r). Another fella got locked out of his system altogether. Should I just unload the module?

Sorry I'm such a dope about this. Thanks for working with me.

---

### Post by max1e6 on 2010-06-26
Thanks, you're a genius! I cannot seem to crash it now.

---

