---
title: "Does GRUB2 support &quot;profile&quot; command when booting?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-05
Just wanted to know if this is still the same as before.

---

### Post by VMC on 2009-10-05
I don't know what this is. Never used it. Here is a [comparison]("http://grub.enbug.org/CommandList") between grub-legacy and grub2.

---

### Post by psyke83 on 2009-10-05
I'm not sure, but... Karmic uses sreadahead instead of readahead. If sreadahead does not support boot-time profiling, it's obviously not going to work.

---

### Post by emarkay on 2009-10-05
Data on Boot Profile originally found here:

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by VMC on 2009-10-05
> **emarkay said:**
> Data on Boot Profile originally found here:

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

Thanks for that link. First time I read about it. Learn something new everyday, but as psyke83 stated, that link references readahead.

---

### Post by psyke83 on 2009-10-06
I believe that sreadahead will automatically profile your system. Recent behaviour was for sreadahead to re-profile after major dist-upgrades, but I'm not sure if that behaviour was modified. 

Either way, I don't think that you need to manually profile anymore.

---

### Post by MacUntu on 2009-10-06
> **psyke83 said:**
> Either way, I don't think that you need to manually profile anymore.

Yep, that's the point. You still can force profiling for the next boot by removing the pack file (list of files to read) at '/var/lib/sreadahead/pack'.

---

### Post by moore.bryan on 2009-10-19
Do you fine folks know of a way to specify how often "re-profiling" should take place; e.g., every twenty boots?

---

