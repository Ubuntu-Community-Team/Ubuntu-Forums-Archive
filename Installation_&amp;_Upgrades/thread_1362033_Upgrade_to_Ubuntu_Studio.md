---
title: "Upgrade to Ubuntu Studio"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by jcc123 on 2009-12-22
Hello, im wondering if somebody could help me by telling me how I can upgrade from Ubuntu 9.10 to Ubuntu Studio 9.10. I'm kind of new in the ubuntu world so I would apreciate any help. Thanks.

---

### Post by bluesscream on 2009-12-22
[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

good luck :)

---

### Post by jcc123 on 2009-12-22
Thanks,,, it was really helpful.

---

### Post by jimbojones666 on 2009-12-22
What's the difference between the two?

---

### Post by bluesscream on 2009-12-23
> What's the difference between the two? 
Main difference is the realtime kernel for ubuntustudio. You may have to do some configuration too, but then you can run audio applications smoothly with very low latency, i.e. very little time lag between input and output signals.
This rt-kernel is less suited for standard apps, networking, gaming etc.

---

### Post by Presario on 2009-12-24
> **bluesscream said:**
> Main difference is the realtime kernel for ubuntustudio. You may have to do some configuration too, but then you can run audio applications smoothly with very low latency, i.e. very little time lag between input and output signals.
**This rt-kernel is less suited for standard apps, networking, gaming etc.**

I understand bout latency and real time is really good for these stuff. But like you said, what do you mean by **less suited**?

Because the problem is that I'm never lucky with Alternate DVD installations haha. I can't get the sound/wireless lan to work (even after days of researching). So I did a normal Ubuntu installation and all worked perfectly (so far). Even live CDs can get the wireless and sound to work properly.
So I decided from here with MOST hardware all recognized, I'd upgrade it to the "Studio" version.

So after upgrading, the latency will improve I guess? and what about the other "standard" apps? Will I experience a degrade in performace with the RT Kernel?

Cheers!:guitar:

---

### Post by bluesscream on 2009-12-24
It's no real upgrade. You'll install a lot of audio, video, graphics stuff from repos and esp. this rt-kernel.
With rt-kernels I had some troubles with my nvidia card and wireless, but these were solved after some days. If you realize troubles on rt-kernel you can boot into generic, it will not be deleted automatically, so it's no risk.
> Will I experience a degrade in performace with the RT Kernel?
I don't think so, but it depends from the apps you use. 
I don't see any necessity for installing entire ubuntustudio/rt-kernel as long as you don't need jackd for audio production or live performance. Just apt-get or synaptic the single apps you need. I made some tests today with different kernels and it seems to me the difference between generic and rt-kernels is melting down.

---

