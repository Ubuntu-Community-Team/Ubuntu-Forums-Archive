---
title: "linux-image upgrade doubt"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by vj358 on 2011-07-26
Hi All, 

I am in the process of recompiling my kernel which I will be doing in the next few days.
I am on Ubuntu 10.10
My previous kernel was 2.6.35-28-generic-pae

So, I tried the first option.
doing it from synaptic, I upgraded to 2.6.35-30, The upgrade was swift & now I am on
uname -r 
2.6.35-30-generic

Doubt 1: Installing it from synaptic only installs a binary image ? 
It doesn't recompile the kernel right ?

Doubt 2: Earlier, ATI's proprietary driver were installed. But with this new kernel image, they aren't.
So I understand that I have to reinstall them. The doubt is, even now I am getting a complete gui. Although
I am not able to test OpenArena or even glxgears, but I am able to see a complete UI
So, in this scenario, is the default XServer working behind ?  and/or the ati's open source drivers are automatically installed ?

The output of dmesg | grep drm is blank.
& there is no interrupt registered for the ati card, which means definitely the open source drivers didn't install. So its only the XServer. 

Output of glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15


Thanks.

---

### Post by vj358 on 2011-07-28
Anyone ?

---

