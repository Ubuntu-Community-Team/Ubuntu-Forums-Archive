---
title: "What machine can Ubuntu Gutsy Gibbon 64-bit edition be installed?"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by zhouxing on 2007-12-26
I am intending to invest on a 64-bit cpu laptop. But I am not sure which CPU is suitable for running 64-bit gutsy gibbon.

One of my friend has a Intel Duo Core Toshiba laptop. I first tried to install 64-bit gutsy but it says it can not.

I am wondering whether only AMD64, Athon 64, Athon 64 X2 and Turion 64 X2 can run 64-bit gutsy.

Any one using 64-bit gutsy please kindly post your configuration of PC here. Thanks!

---

### Post by ahaslam on 2007-12-26
It should run on any Intel Core **2** Duo processor.

---

### Post by LaRoza on 2007-12-26
AMD64 is misleading, it runs on any x86_64 processor. (As opposed to IA-64, which you would know if you had)

Intel Core and Intel Core 2 are different. Core 2 is 64 bit, Core is not.

---

### Post by zhouxing on 2007-12-26
What is the advantage of 64-bit Ubuntu over 32-bit Ubuntu? Is is faster? What about the application compatibility issue?

---

### Post by JangMunho on 2007-12-26
Linux x86-64 supports any x86-64 CPU, which includes Intel EM64T, AMD64.
Core Duo is not a 64-bit CPU. You can check if your CPU support x86-64 through CPU-Z.

I'm using ubuntu 7.10 64-bit, and I also used 32-bit ubuntu 7.10.
I feel the 64-bit version is faster. (Maybe just a feeling...) And all the applications work well, most of which are 32-bit applications.
I even compiled wine by myself and it works perfectly though it cannot show Chinese characters after I've tried every method offered on the internet...

So you see, linux 64-bit have the binary capatibility to 32-bit software. It's wonderful.

PS: happy to meet a Chinese friend in this forum... :-)

---

### Post by zhouxing on 2007-12-26
Happy to meet a chinese friend here too! 

I guess the my friend's laptop is a intel duo core, not a core 2. haven't got a chance to run CPU-Z on his machine yet. hehe...

I had installed virtual box running XP in ubuntu. it works fine. any problem I need (like AutoCAD 2007) and not available in Ubuntu, I put them there.

wine has a lot of problem with chinese characters. I only run Thunder english version in ubuntu in wine, but sometimes menu disappears.

---

### Post by ahaslam on 2007-12-26
> **zhouxing said:**
> What is the advantage of 64-bit?
For me it's multimedia performance. For example, encoding an HD movie in x264 is about 20% faster.

---

