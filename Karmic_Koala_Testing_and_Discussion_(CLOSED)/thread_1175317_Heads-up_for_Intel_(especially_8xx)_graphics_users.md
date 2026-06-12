---
title: "Heads-up for Intel (especially 8xx) graphics users"
date: 2009-06-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by psyke83 on 2009-06-01
[This]("http://ubuntuforums.org/showpost.php?p=7380051&postcount=623") post will be of interest to you folks...

---

### Post by Kareeser on 2009-06-01
Hrm? I've had great* performance on my 855GM ever since I installed 2.6.30-rc5...

[size=1]* I still can't utilise the VGA output on my laptop... though... [/size]

---

### Post by psyke83 on 2009-06-01
> **Kareeser said:**
> Hrm? I've had great* performance on my 855GM ever since I installed 2.6.30-rc5...

[size=1]* I still can't utilise the VGA output on my laptop... though... [/size]

Tiling should have been broken for your chipset, which would have constrained performance somewhat. Did you notice that glxgears yielded a corrupt image? Or did you disable tiling in your xorg.conf?

---

### Post by Kareeser on 2009-06-01
Neither, actually. glxgears ran great... still does, here :)

---

### Post by psyke83 on 2009-06-01
> **Kareeser said:**
> Neither, actually. glxgears ran great... still does, here :)

Ah yes, now I understand. You're using EXA acceleration (which also means DRI1). I'm talking about UXA & DRI2 (which will be the only possible combination with the intel 2.8.0 driver).

---

### Post by Kareeser on 2009-06-01
I see... well, in any case, good to hear, thanks for sharing :)

EXA seems to be enabled by default, and I don't think my card supports DRI2. Hrm..

---

### Post by hexion on 2009-06-02
What's the difference between sarvatt's kernel and kernel PPA's one (apart from KMS)?
Too bad there's no sarvatt's kernel built for amd64 to give it a shot though..

---

### Post by psyke83 on 2009-06-02
> **hexion said:**
> What's the difference between sarvatt's kernel and kernel PPA's one (apart from KMS)?
Too bad there's no sarvatt's kernel built for amd64 to give it a shot though..

The -sarvat2 kernel was built just after Linus pushed some DRM fixes (May 27th, though according to Eric Anholt's site, the important fixes were merged on the 29th). See: [http://www.phoronix.com/forums/showpost.php?p=76563&postcount=221](http://www.phoronix.com/forums/showpost.php?p=76563&postcount=221)

The next time Karmic gets a kernel update - i.e., based on rc8 - these specific fixes should be included.

---

### Post by psyke83 on 2009-06-03
A quick update: I notice that Bryce has uploaded libdrm with some important fixes and the latest intel driver from git. This now means that EXA and DRI1 are no longer supported, so UXA and DRI2 is now the default setting :).

For owners of the older 8xx chipsets, you'll need to wait for the next kernel update to avail of the crucial fixes mentioned in Eric Anholt's blog - or you can use the 2.6.30-rc7-sarvatt2 kernel (see the earlier link for details).

---

### Post by ghindo on 2009-06-03
Thanks for keeping us updated, psyke83 :)

---

### Post by andrewabc on 2009-06-03
> **psyke83 said:**
> A quick update: I notice that Bryce has uploaded libdrm with some important fixes and the latest intel driver from git. This now means that EXA and DRI1 are no longer supported, so UXA and DRI2 is now the default setting :).

For owners of the older 8xx chipsets, you'll need to wait for the next kernel update to avail of the crucial fixes mentioned in Eric Anholt's blog - or you can use the 2.6.30-rc7-sarvatt2 kernel (see the earlier link for details).

Let us know when this is incorporated into 9.10. Hopefully in time for alpha 2 (June 11)?
I want to test out these new technologies from liveusb. I'm using g965 x3000, and video works fine for me in 9.04, so I dunno if I'll notice any performance enhancements.

---

### Post by vaibhav on 2009-06-03
-rc8 is now out.

---

### Post by Vanishing on 2009-06-03
and its still not working.

---

