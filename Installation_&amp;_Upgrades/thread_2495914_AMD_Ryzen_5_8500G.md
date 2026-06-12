---
title: "AMD Ryzen 5 8500G"
date: 2024-03-07
forum: Installation &amp; Upgrades
---

### Post by Robk29 on 2024-03-07
Hello all,

                        I’m wondering if anyone can offer any experience they may have with the AMD Ryzen 5 8500G with integrated Radeon 740M (or D per another source) graphics. I build myself a new desktop every 3 years and decided to ‘future proof’ my setup (to some extent) with AM5 which supports DDR5 RAM.

 
 
 The CPU is quite new (31 Jan  2024) so I won’t push the envelope with 24.04 LTS but will install 22.04.4 LT, always happy to stay slightly behind the release curve. With my previous build the generic graphics driver caused a basic game that I play (Wargame Red Dragon) to ‘stutter’ and I was forced to load the NVIDIA proprietary driver to solve it.

 
 
 Any comments or experience with this CPU?

---

### Post by TheFu on 2024-03-07
Not me.  

Any really new CPU will need the latest kernel, so the idea that you'll be able to install 22.04 would be the first thing I'd check.  You may need 23.10 or have to wait for 24.04 to be released (if you don't run the alpha).   Best to be at least 1 yr behind on any new hardware to give the different F/LOSS projects time to catch up.  For example, don't expect any sensors to work.
Also, I had to move kernels do get my Ryzen iGPU supported. For months, I ran with VESA-only iGPU graphics until I was prepared to move to a new release.

For example, 
> Ubuntu 23.10 with the Linux 6.7 kernel and Mesa 24.1-devel were used for benchmarks here: [https://www.phoronix.com/review/amd-ryzen-5-8500g](https://www.phoronix.com/review/amd-ryzen-5-8500g)  24.1-devel means he probably needed to build the Mesa libraries.

Part of me is jealous.  Part of me is worried that you are jumping a year too soon.

---

### Post by Robk29 on 2024-03-07
Thanks TheFu,

Moving too early is what I'm worried about too. AMD offers no guidance other than to say Ubutnu being supported (It's silent on the versions).

I feel that I may need to run with 23.10 as you suggested so I'll need to be prepared for that, thanks. What I don't want to do (for example) is install Win 11 and source a TPM for the interim period or juggle legacy Ubuntu versions hoping to find a good fit. Saying that, I may have to.

Thanks again.

---

### Post by Robk29 on 2024-03-11
For anyone that might be interested, AMD support have advised that the latest LTS is recommended which literally means 22.04 today, what happens on and after 25 April 2024 is unknown. TheFu suggested 23.10 and this may still be an option.

---

### Post by xeghepgiare on 2024-03-11
I'm also interested.
Thank you.

---

