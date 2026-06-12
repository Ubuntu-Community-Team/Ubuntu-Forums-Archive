---
title: "Kernel for SMP (?)"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by BadRambo on 2006-09-24
Hello All ---

Just loaded my first copy of Ubutu, which came in the back of a third party book (not sure if it is really up to date) --- but I noticed that comments said that Ubutu would sense the presence of a dual core/CPU device and load the appropriate kernel, BUT my version just loaded what appears to be the only one it had -- a single CPU kernel.

Is there an installer around for an SMP kernel, and do I really have the latest and greatest version, which was marked "ver. 1.0" when I see much higher versions out there???

Suggestions/comments please!  Thanks --- Bob --- :|

---

### Post by jpkotta on 2006-09-24
The default Dapper kernel is SMP.  To check, do ```
less /proc/cpuinfo
``` and it should mention more than one processor (if you have more than one).

---

### Post by BadRambo on 2006-09-24
Unfortunately, I have a version that does not have SMP capability, and only a single CPU (core) is recognized. And, at the same time, when I check out the "About Unbuntu" information, it makes note of the fact that I have the Dapper version??? This is strange, because I also did a search for other kernel source, and nothing --- just the single CPU kernel now installed. Guess I need to download a "real" Dapper .iso image and make a CD....

Am I missing something here in this release ?? 

Recommendations??? --- Thanks --- Bob --- ;)

---

### Post by jpkotta on 2006-09-24
Strange.  If you do ```
sudo apt-get install linux-686-smp 
``` you should get the latest SMP kernel (the 686 refers to Pentium II or better).

---

