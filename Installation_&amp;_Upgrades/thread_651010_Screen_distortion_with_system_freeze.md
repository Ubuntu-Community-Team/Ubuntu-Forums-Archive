---
title: "Screen distortion with system freeze"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by partriv on 2007-12-27
Hi all,

Since upgrading to gutsy (using the auto gui system updater) i have had a slew of problems, the final of which the system hard freezes after what i can figure to be lots of video/graphics usage.  It doesn't take much time for this to happen either.  The screen completely changes, often going white or grey with some black lines horizontally across it.  

I have used the restricted drivers manager and got the new glx drivers installed.  It doesnt seem to be helping the situation though.  Any ideas or ways i can start debugging this?  Any suggested logs i may look at to get some more indications of why the system is freezing?

Thanks

---

### Post by partriv on 2007-12-27
here is a picture of what happens on the monitor

---

### Post by partriv on 2007-12-27
bump... any ideas on how i can even begin debugging this?

---

### Post by partriv on 2007-12-28
Well it appears that the nvidia drivers are what is causing this.  I am now on the vesa drivers and it appears to be working fine, though I don't think it is supporting 3d acceleration now.  For the time being this is fine since it is a development machine anyway, but does anyone know why the new (and old) nvidia drivers (running under gutsy) are causing this problem?

---

### Post by Mago on 2008-03-09
I have the exact same problem... it's completely random, but compiz seem to trigger it every time after 5 to 10 mins
using lower resolutions with the nv driver seems to work.
by the way i'm now having the same behavior with windows xp so it's either something with the newer nvidia drivers or it's hardware related... anyway i can't figure it out

system spec:
athlon 3000+
asus a8n-vm csm (geforce 6150)
1gb ddr 400

---

