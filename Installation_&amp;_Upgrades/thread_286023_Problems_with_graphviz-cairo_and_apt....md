---
title: "Problems with graphviz-cairo and apt..."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Gsundbrunn on 2006-10-27
Hi,

I currently use Edgy and have a little problem after installing some applications especially cairo caused an error I cannot fix anymore. No need to get it run anyway - but everytime I use apt or synaptic I receive this error (sorry - using a german version - but the code and the error should be the same in german).

E: graphviz-cairo: Unterprozess post-removal script gab den Fehlerwert 127 zurück

How can I completely remove the installation to get rid of this message?

Thanks in advance!

Stefan

---

### Post by arm73c05 on 2006-11-01
this worked for me (on edgy/powerpc):

sudo rm /var/lib/dpkg/info/graphviz-cairo.post*
sudo aptitude remove -f graphviz-cairo

seems 'dot' was unavailable, causing the post install/removal scripts to fail..

---

### Post by nikopol on 2006-11-01
nice one! Thanks for that.

---

### Post by dismalperception on 2006-11-06
YES!!! I have gone practically bald trying to figure out what was wrong with my system.  THANKS!](*,)

---

### Post by &amp;wi*m#~10+q on 2007-02-05
> **arm73c05 said:**
> this worked for me (on edgy/powerpc):

sudo rm /var/lib/dpkg/info/graphviz-cairo.post*
sudo aptitude remove -f graphviz-cairo

seems 'dot' was unavailable, causing the post install/removal scripts to fail..

thanx :P

---

### Post by DigitEyez on 2007-02-07
That worked just fine thanks.

---

### Post by wit_273 on 2007-03-19
I have been racking my skull for 2 weeks trying to figure this one out.  I have looked at every forum I could find with many suggestions-- none the were good.  This one worked.  Thanks soooo much.  I was about to result to the old MS solution-- reload.

---

