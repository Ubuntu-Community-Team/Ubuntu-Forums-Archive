---
title: "Firefox JavaScript performence is still terrible"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phrostbyte on 2010-04-12
Compare Chromium and the default Firefox included in Ubuntu (64-bit).

Firefox 3.6 seemingly shows little improvement over Firefox 3.5 despite (apparently), the JavaScript JIT'er being enabled in 3.6 builds. I was expecting at least a 2x improvement on SunSpider.

---

### Post by lovinglinux on 2010-04-12
If you are running 64bit version of Firefox, then it seems JIT is not enabled.

---

### Post by FFuser on 2010-04-12
I've tested sunspider 0.9.1 in both firefox 3.6 (from mozillateam-stable), firefox 3.7 (from mozilla daily) and chromium (nightly build) on Karmic on 64bit

Firefox 3.6 2423ms
Firefox 3.7 1133ms (x2.14)
Chromium     446ms (x5.43 compared to 3.6, 2.54 compared to 3.7)

So it seems that their is a vast improvement to be expected in the next firefox, but it is still not as fast as webkit/chromium.

---

### Post by linusr on 2010-04-12
> **FFuser said:**
> I've tested sunspider 0.9.1 in both firefox 3.6 (from mozillateam-stable), firefox 3.7 (from mozilla daily) and chromium (nightly build) on Karmic on 64bit

Firefox 3.6 2423ms
Firefox 3.7 1133ms (x2.14)
Chromium     446ms (x5.43 compared to 3.6, 2.54 compared to 3.7)

So it seems that their is a vast improvement to be expected in the next firefox, but it is still not as fast as webkit/chromium.

wait till FF 3.7!!! Chrome is lookn gud but too many crashes lately..

---

### Post by lovinglinux on 2010-04-12
> **linusr said:**
> wait till FF 3.7!!! Chrome is lookn gud but too many crashes lately..

Specially now that Mozilla is bringing Lorentz's plugin isolation to the table ;)

---

### Post by kahumba on 2010-04-12
JIT was never enabled in 64 bit Firefox, it will only ship enabled by default starting with version 3.7, because Mozilla is only lately starting to take 64bit OSes for serious, shame on them, who knows, if it wasn't for the native 64 bit Chrome on Linux maybe they wouldn't have bothered at all.

---

### Post by linusr on 2010-04-12
> **kahumba said:**
> JIT was never enabled in 64 bit Firefox, it will only ship enabled by default starting with version 3.7, because Mozilla is only lately starting to take 64bit OSes for serious, shame on them, who knows, if it wasn't for the native 64 bit Chrome on Linux maybe they wouldn't have bothered at all.

32-bit FF is really slow on pages using JS... not sure how bad 64-bit FF can be

---

### Post by kahumba on 2010-04-12
> **linusr said:**
> 32-bit FF is really slow on pages using JS... not sure how bad 64-bit FF can be

1) True, compared to the window$ counterpart. The Linux version of FF 32 bit is slower than the window$ version by well, like 5-30% depending on what, how and where you're benchmarking.
2) True, compared to the likes of Google Chrome.
3) Not true, compared to IE6-8.

---

