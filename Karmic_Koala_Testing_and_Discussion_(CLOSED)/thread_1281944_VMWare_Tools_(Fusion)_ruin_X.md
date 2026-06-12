---
title: "VMWare Tools (Fusion) ruin X"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by N74JW on 2009-10-03
Hello,

I am not exactly sure where this information belongs, so I will post it here...

I was testing the beta for 9.10 in a VMWare Fusion virtual machine on my Mac.  When installing the VMWare tools, the final part rewrites the xorg.conf file, which renders the VM without any X environment. This happened on two separate occasions.  I am using VMWare Fusion 2.0.5 on a late gen. iMac 24".

Workaround: Skip the xorg.conf step of the VMWare tools installer script, which is the final part.  Pay attention during the various config. questions an DO NOT rewrite the xorg.conf file and you'll be fine.

---

### Post by mfox on 2009-10-04
Unfortunately, your solution did not work for me.  I was using Fusion 2.0.6 on a 1,83 ghz core 2 duo mac mini running Snow Leopard 10.6.1.  I tried installing the 9.10 beta several different ways: automatic and manual, adding the tools before and after updating the beta, and with and without adding build-essential.  The installation itself resulted in a Desktop upon reboot, but no matter what I did after that, I got a black screen after that next step.  Ironically, I didn't have this problem with the alphas, albeit on a different mac (iMac with nvidia 9400 video card) and using the VMware Fusion 3 beta.

---

### Post by N74JW on 2009-10-04
I am going to try on my MacBook Pro (9400M / 9600M GT)

---

### Post by mfox on 2009-10-23
The problem seems to be fixed in Karmic RC, at least when I run the tools and don't let it create a new xorg.conf.  I didn't try letting it do so; that might now be OK.

---

