---
title: "desktop running slow after 7.10 install"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by hodad on 2007-11-02
I just installed 7.10 fresh last week on my AMD64 machine.  I also installed a newer, larger hard drive, and installed 7.10 onto it.  I can still access the older drive, and have transferred my older files onto the newer drive.  

Everything works fine, but it runs VERY SLOW!

A few more details:
Running System Monitor shows no unusual activity (cpu and memory running about 30% when I start Open Office, and less when idle).
I suspect it has something to do with the second drive, but I can disconnect the second (smaller) drive connector, and the pc boots up just fine, albeit still slow.   

Is there some process that is eating up cpu time that doesn't show on the system monitor?   Do I need to eliminate the second drive (I'd like to keep it to backup files onto,however).

Thanks

---

### Post by cuby on 2007-11-03
Try powertop to check the system calls:

```
sudo powertop
```

check: [http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by hodad on 2007-11-04
I downloaded and tried to compile, but got a welter of error messages, looks like I need to have a bunch of libraries, but I never seem to have any success when I get that deep into it.   Is there any way I can install powertop thru Synaptic?  Can't find it under synaptic; do I need to enable a repository?
Thanks

---

### Post by cuby on 2007-11-04
Yes... I think so...
try
```
sudo apt-get install powertop
```

or search in the synaptic

---

