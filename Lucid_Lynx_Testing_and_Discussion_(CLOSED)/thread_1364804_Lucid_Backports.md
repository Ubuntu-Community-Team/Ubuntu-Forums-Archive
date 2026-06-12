---
title: "Lucid Backports"
date: 2009-12-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dgoldb1 on 2009-12-26
I am trying to get my internal wifi working with Lucid with little success.  My internal wifi is an atheros AR5001X+.  I heave read that installing the backports may resolve this issue.  I have enabled backports in Software Sources but I am unable to download them.  I have tried:

sudo aptitude install linux-backports-modules-karmic
sudo aptitude install linux-backports-modules-lucid

Both return back with unable to find package.  How can I load backports to get my internal wireless working?

Thanks.

---

### Post by xebian on 2009-12-26
> **dgoldb1 said:**
> I am trying to get my internal wifi working with Lucid with little success.  My internal wifi is an atheros AR5001X+.  I heave read that installing the backports may resolve this issue.  I have enabled backports in Software Sources but I am unable to download them.  I have tried:

sudo aptitude install linux-backports-modules-karmic
sudo aptitude install linux-backports-modules-lucid

Both return back with unable to find package.  How can I load backports to get my internal wireless working?

Thanks.

IIRC backports are newer packages for an older release.  Lucid is still being worked on and no releases except the alpha's.  So where do you think these 'backports' are coming from?  ;)

---

### Post by dgoldb1 on 2009-12-26
So any recommendations on how to get my Atheros controller working in Lucid?

---

### Post by jakeeee on 2010-04-24
I would like to know this too.
Anyone know?

---

### Post by vredley on 2010-04-24
Try linux-backports-modules-wireless-lucid-generic.

---

### Post by jakeeee on 2010-04-24
Thank you!!!

---

