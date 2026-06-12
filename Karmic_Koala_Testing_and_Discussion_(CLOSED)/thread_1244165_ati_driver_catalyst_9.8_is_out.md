---
title: "ati driver catalyst 9.8 is out"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-08-19
ati driver catalyst 9.8 is out. will this driver be as fglrx in Karmic?

---

### Post by dinxter on 2009-08-19
as i understand it the 2.6.31 kernel wont be supported until catalyst 9.10, which is supposed to be available in time for karmic release. 9.8 supports up to kernel 2.6.30 although it and the driver in the repository can be made to 'work' for the moment in karmic

---

### Post by BbUiDgZ on 2009-08-19
> **dinxter said:**
> as i understand it the 2.6.31 kernel wont be supported until catalyst 9.10, which is supposed to be available in time for karmic release. 9.8 supports up to kernel 2.6.30 although it and the driver in the repository can be made to 'work' for the moment in karmic
anyone know if this will work with the x600?

---

### Post by alphacrucis2 on 2009-08-19
> **BbUiDgZ said:**
> anyone know if this will work with the x600?

I thought AMD dropped those with Catalyst 9.4.

Just confirmed. If you go to AMD's driver website and navigate to where to download drivers for your card. It offers the legacy Catalyst 9.3 version which means your card is considered legacy by AMD. Unfortunately the Catalyst 9.3 version of fglrx doesn't work with the X.org version in Jaunty or later. The good news is that the Open source drivers for these older cards are getting better all the time.

---

### Post by ssri on 2009-08-19
> **alphacrucis2 said:**
> I thought AMD dropped those with Catalyst 9.4.

Just confirmed. If you go to AMD's driver website and navigate to where to download drivers for your card. It offers the legacy Catalyst 9.3 version which means your card is considered legacy by AMD. Unfortunately the Catalyst 9.3 version of fglrx doesn't work with the X.org version in Jaunty or later. The good news is that the Open source drivers for these older cards are getting better all the time.

Got catalyst 9.3 to work in Jaunty by downgrading xserver.  Now googleearth and nexuiz run pretty fast.  However, the next wall is that Catalyst 9.3 only supports kernels <2.6.29.  So, with Karmic, I'll have to ditch ATI's proprietary drivers forever.  I cannot say that I will unhappy when the day comes.  I'm only hanging onto Catalyst for its ridiculously easy TV-out setup.  It seems that there are still issues with TVOut for the R500s in opensource drivers.

---

### Post by petri on 2009-08-19
No show in Karmic on my 4850 on crossfire with Catalyst 9.8 :---)


With Jaunty it works.

---

### Post by uBeer on 2009-08-19
> **dinxter said:**
> as i understand it the 2.6.31 kernel wont be supported until catalyst 9.10, which is supposed to be available in time for karmic release. 9.8 supports up to kernel 2.6.30 although it and the driver in the repository can be made to 'work' for the moment in karmic

Could you please elaborate on getting the driver to 'work'??

---

### Post by dinxter on 2009-08-19
> **uBeer said:**
> Could you please elaborate on getting the driver to 'work'??

its all in the link below
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394985](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394985)

---

### Post by uBeer on 2009-08-19
Thanks, I'll try it out tonight and report back if it works or not.

---

