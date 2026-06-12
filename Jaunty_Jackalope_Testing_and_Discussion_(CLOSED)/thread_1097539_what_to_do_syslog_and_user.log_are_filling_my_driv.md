---
title: "what to do? syslog and user.log are filling my drive with..."
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-03-16
> Mar 16 09:22:46 jaunty-5 pulseaudio[4689]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053432127412 bytes (418283028676 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.

Cheers, Mike

---

### Post by taavikko on 2009-03-16
Upgrade to fix that is been released and available in main repos.

You could also nullify those files, if space is an issue
```
echo "" |sudo tee /var/log/{user.log,user.log.0,syslog,syslog.0}
```

---

### Post by mdurham on 2009-03-16
> **taavikko said:**
> Upgrade to fix that is been released and available in main repos.


Thanks for that taavikko, I've just done an update, maybe that will fix it. Do you know when the fix was released?
Cheers, Mike

---

### Post by klange on 2009-03-16
Trust me, your log isn't that big:
13 835 058 053 432 127 412 bytes = 12 582 912 terabytes

---

### Post by mdurham on 2009-03-16
> **klange said:**
> Trust me, your log isn't that big:
13 835 058 053 432 127 412 bytes = 12 582 912 terabytes
No no, that was just the error message. The error message was being written thousands of times thus reducing the free space on the disc. Trust me too!
Cheers, Mike

---

### Post by crimsun on 2009-03-16
> **mdurham said:**
> Thanks for that taavikko, I've just done an update, maybe that will fix it. Do you know when the fix was released?
Cheers, Mike

Bugs [320875]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/320875") and [343254]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/343254") were fixed Saturday and uploaded yesterday.

---

### Post by mdurham on 2009-03-16
> **crimsun said:**
> Bugs [320875]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/320875") and [343254]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/343254") were fixed Saturday and uploaded yesterday.

Thanks crimsun

---

