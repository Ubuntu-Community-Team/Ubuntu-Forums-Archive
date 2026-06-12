---
title: "Ubuntu and EM64T"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by kahping on 2005-03-20
i've been wondering about this for some time now.

if i wanted to install Ubuntu on one of those new Intel chips with EM64T, should i install Ubuntu x86 or AMD64? since Intel's 64bit extensions are nothing but a "clone" of AMD's x86_64, would that mean that i can install Ubuntu AMD64 on a EM64T capable machine?

kahping

---

### Post by DJ_Max on 2005-03-20
Intel & AMD are under the x86 arch, so Intels 64bit processors would use the x86_66, Ubuntu labels it AMD64, as most users are familar with the name.

So use AMD64, unless you have an Itanium processor. [http://releases.ubuntu.com/5.04/](http://releases.ubuntu.com/5.04/)

Also a little info on Intels EMT64, it's isn't really a clone of AMD64, since the **early** EMT64 processors weren't true 64bit, rather "emulating" 64bit over a true 32 bit. EM64T is an extension to Intel's processors based on the IA-32 architecture. Not until recently have they showed the true 64bit processors for their EMT64(Extended Memory Technology 64) line. But haven't been released yet.

This info can be found on Intel's website.

Performance wise, I don't know if it'll make a difference, as I haven't bence marked them against the AMD64's. Even so, unless your a hard-core gamer, it shouldn't matter.

---

### Post by kahping on 2005-03-21
thanks for the explanations, DJ_Max.

what do you mean by "early EMT64 processors"?

i remember reading somewhere that Pentium 4 5xx series processors had EM64T but that it was disabled. only with the newer 6xx series it's enabled. is this what you meant by "early EMT64 processors"?

kepp in mind, i'm not entirely sure if i really read it somewhere or if my mind just made it up though  :-P 

kahping

---

### Post by DJ_Max on 2005-03-21
Yeah, thats basicly what I meant, as Intel plans to release their 'true' 64 bit processors soon. As I don't have an exact date, don't know if they decided to release them.

---

