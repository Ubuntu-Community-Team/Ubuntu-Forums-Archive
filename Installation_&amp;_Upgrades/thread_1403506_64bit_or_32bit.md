---
title: "64bit or 32bit ?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by badspell68 on 2010-02-10
I have a new Sony laptop with 64 bit win 7. Can I install 32bit Ubuntu, how and what problems may I face with the boot process and Win 7?

---

### Post by wojox on 2010-02-10
Sure you can install 32 bit, but 64 bit is better. ;)

---

### Post by Grenage on 2010-02-10
You should have no issues with Win7.  If your machine has over 3GB of RAM then go x64.  It won't make much difference either way if you don't.

---

### Post by l3git.h4cker on 2010-02-10
> **wojox said:**
> Sure you can install 32 bit, but 64 bit is better. ;)
I'm gonna have to disagree with you there.
I have tried both, and though faster,  64 bit has a lot of compatability issues (with my hardware at least).
My recommendation is to stick with 32 bit.

---

### Post by badspell68 on 2010-02-10
What about boot process and will Win7 be different then setting up with XP? Any recommendations?

---

### Post by khelben1979 on 2010-02-12
> **badspell68 said:**
> What about boot process and will Win7 be different then setting up with XP? Any recommendations?

I would recommend to have Windows and Linux on 2 separate harddrives. Makes it easier, in my opinion.

---

### Post by lukeiamyourfather on 2010-02-12
> **khelben1979 said:**
> I would recommend to have Windows and Linux on 2 separate harddrives. Makes it easier, in my opinion.

Its a laptop, not a desktop. Dual booting with Windows 7 should work just fine with Ubuntu. I'd go with 64-bit if the hardware supports it. Cheers!

---

### Post by jenaniston on 2010-02-12
> **badspell68 said:**
> I have a new Sony laptop with 64 bit win 7. Can I install 32bit Ubuntu, how and what problems may I face with the boot process and Win 7?

I'll chime in from my experience with U9.04 32 bit on an amd64 laptop - it ran fine but ***cooked*** the cpu.

While it ran Ubuntu 9.04 ok . . . the fan immediately came on.
I downloaded lm-sensors and checked cpu temperature and could get to 80+ C.

With 64 bit U9.04 that cpu temp was around 47 C.  - maybe an anecdotal and isolated incident for other reasons -
but don't burn up the cpu with 32 bit is my 2¢  . . .
any potential compatability or bug issues of the 64 bit versions aside.

---

### Post by badspell68 on 2010-02-12
Burn up the CPU...That seems unlikely.

---

### Post by lukeiamyourfather on 2010-02-12
> **jenaniston said:**
> I'll chime in from my experience with U9.04 32 bit on an amd64 laptop - it ran fine but ***cooked*** the cpu.

While it ran Ubuntu 9.04 ok . . . the fan immediately came on.
I downloaded lm-sensors and checked cpu temperature and could get to 80+ C.

With 64 bit U9.04 that cpu temp was around 47 C.  - maybe an anecdotal and isolated incident for other reasons -
but don't burn up the cpu with 32 bit is my 2¢  . . .
any potential compatability or bug issues of the 64 bit versions aside.

The CPU was not running hot because it was running 32-bit software, something else was causing the issue.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

Modern amd64 processors (x86_64) are designed to natively run both 32-bit and 64-bit software without issue. Cheers!

---

### Post by jenaniston on 2010-02-12
> **badspell68 said:**
> Burn up the CPU...That seems unlikely.

OK, burn any papers the laptop sits on . . . and your hand next to the laptop then
  -or . . . just use the laptop to fry eggs and make some instant coffee then too.

But the constant fan would be plenty enough reason  . . . ***obviously*** it stressed the cpu
and benchmark tests waaaay better too with 64 bit versions.

I'd vote 64 bit for better cpu performance by far - regardless if you like 85 C. -
and failure is only at 95 C.

---

### Post by khelben1979 on 2010-02-12
> **lukeiamyourfather said:**
> Its a laptop, not a desktop. Dual booting with Windows 7 should work just fine with Ubuntu. I'd go with 64-bit if the hardware supports it. Cheers!

Hmm.. well, it's possible to attach an external usb harddrive and install on that one, making it a dualboot system. But you're right on how I was thinking and since it's a laptop it's probably better not to, I guess.

---

### Post by jenaniston on 2010-02-12
> **lukeiamyourfather said:**
> The CPU was not running hot because it was running 32-bit software, something else was causing the issue.
  

But then, running the 64-bit distribution of linux instead of the same distribution 32-bit version
then made ***that issue*** lead to a 40 degrees cooler cpu - so all was better in this case.

cpu processes and utilization would be better with 64-bit . . .
 so it still makes sense - and the cpu wouldn't need the fan running so **LOUD** in the library.

So 64 bit is ultimately . . . *quieter*.

---

### Post by northrup on 2010-02-12
Personally, I prefer 64-bit.  For me, I do actually notice better performance.  Plus, I have a feeling that, once more hardware is supported under 64-bit operating systems, they will start to phase out 32-bit CPUs in performance computing.  I run an Athlon 64 3700 on my desktop.  Works beautifully with 64-bit Ubuntu.

---

### Post by lukeiamyourfather on 2010-02-12
> **jenaniston said:**
> But then, running the 64-bit distribution of linux instead of the same distribution 32-bit version
then made ***that issue*** lead to a 40 degrees cooler cpu - so all was better in this case.

cpu processes and utilization would be better with 64-bit . . .
 so it still makes sense - and the cpu wouldn't need the fan running so **LOUD** in the library.

So 64 bit is ultimately . . . *quieter*.

I have no doubt that 32-bit Ubuntu gave you trouble and the 64-bit version didn't, however that doesn't mean that 32-bit software inherently makes processors run hotter. There was probably a bug that specifically affected your hardware. See the difference?

---

### Post by RedSingularity on 2010-02-12
32bit is good if you have 3 gigs of RAM or less.  If you have anymore you will need 64bit for the system to recognize it.

---

### Post by lenoirrichelieu on 2010-02-13
> **RedSingularity said:**
> 32bit is good if you have 3 gigs of RAM or less. If you have anymore you will need 64bit for the system to recognize it.
 
Not quite true. Ubuntu 32 automatically select PAE-activated kernel if it founds more than 3 Gb RAM installed in order to use all. 
More about PAE can be found at [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

