---
title: "sreadahead"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rtalcott on 2009-09-08
Just downloaded some updates...including 2.26.31-10 and Mr. sreadahead is hogging my cpu...anyone else seeing this?
rt

---

### Post by MacUntu on 2009-09-08
Is this happening after every boot? Do you have a file /var/lib/sreadahead/pack? Just doing updates, will see what happens. :)

---

### Post by rtalcott on 2009-09-08
That was the first boot after the updates...and...after a couple minutes it did stop...I'll see what happens after the next boot...

I have never seen this before.

rt

---

### Post by rtalcott on 2009-09-08
No pack... just a directory /var/lib/sreadahead/debugfs

rt

---

### Post by MacUntu on 2009-09-08
It seems the current pack file (the file list for sreadahead) gets removed with a kernel upgrade so sreadahead will create a new one with the next boot. That worked fine for me, just took something like 20 seconds of higher CPU load on my system.

---

### Post by rtalcott on 2009-09-08
Great!

Thank You for the information!
rt

---

### Post by andresmh on 2009-09-08
I've been experiencing this same thing. I've rebooted multiple times after updating the kernel and it always keeps happening.

---

### Post by rtalcott on 2009-09-08
After a reboot I'm seeing it take up one core for 3-4 minutes...
rt

---

### Post by froggyswamp on 2009-09-09
Same here, x64, hoping for a soon update to fix it (and to fix the fonts in Firefox 3.5.2).

---

### Post by jocko on 2009-09-09
> **froggyswamp said:**
> Same here, x64, hoping for a soon update to fix it (and to fix the fonts in Firefox 3.5.2).
How do you propose an update should fix it??? It's not broken!
**sreadahead is doing exactly what it's supposed to do**. It profiles your boot to update the list of files it should read on boot, in order to be able to boot faster. It only runs after kernel updates (and probably some other important updates). Just relax and let it finish it's job. It really needs to use your cpu for a while. If it wouldn't run you would see boot speed degrading over time as sreadahead would read files that are no longer needed and it would not read files that are needed.

---

