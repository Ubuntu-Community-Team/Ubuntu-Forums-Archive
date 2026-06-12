---
title: "how to replace kernel with synaptic?"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by frank_costanza on 2006-09-29
Hello. I'm a first-time Ubuntu user and installed Dapper on my Compaq V3000 laptop.

By default, Ubuntu installs the 386 kernel. I want to replace that with the kernel compiled for AMD k7 smp (the laptop has a Turion x2).

I used synaptic to install linux-image-2.6.15.27-k7. On reboot, X would not load and I was left at a shell prompt. I verified that the kernel being used was the k7 kernel.

So I restarted and selected the 386 kernel and X still works. Is there something andditional I need to do to change the kernel so that X still works?

Thanks!

---

### Post by kazuya on 2006-09-29
I believe that you may require a 64 bit ubuntu live install CD instead of the basic previous 386 install to take advantage of that CPU.

On that install, you can only use 386, k6, and 686 {recommended.}

But to use the k7, you have to use a different install CD since the apps on that one are designed to match that CPU kernel if I am not mistaken.

So go with getting the 64 bit version.

Hope this helped.

---

### Post by tht00 on 2006-09-30
> **kazuya said:**
> I believe that you may require a 64 bit ubuntu live install CD instead of the basic previous 386 install to take advantage of that CPU.

On that install, you can only use 386, k6, and 686 {recommended.}

But to use the k7, you have to use a different install CD since the apps on that one are designed to match that CPU kernel if I am not mistaken.

So go with getting the 64 bit version.

Hope this helped.

No, the k8 is the 64-bit.  The k7 is installable with the x86 base install.

64-bit is still pretty much just a headache -- don't go down that route unless you're really itching to have 'fun' (see ](*,) ).

---

### Post by frank_costanza on 2006-10-03
Yes, I'm quickly finding out that 64-bit is not as polished.

I got the nvidia driver installed via Automatix.  Everything seems to work ok except suspend (screen never comes back on during resume) and wireless (which was a problem with 32-bit as well).

But, I like the challenge.  I just hope I can get the quirks worked out.

---

