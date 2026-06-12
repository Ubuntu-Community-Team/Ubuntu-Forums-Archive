---
title: "Video driver for display on new installation."
date: 2019-01-15
forum: Installation &amp; Upgrades
---

### Post by mrjacque on 2019-01-15
Have Kubuntu launching from 2 drives. One have used for years, one just installed. 

On the old installation my HP 2009m monitor is detected and I can adjust the resolution. On my new installation it does not recognize my display and only allows a resolution default which makes everything so large that it is un-navigable. 

Is there a file I can copy from my old installation and replace or add to my new to get back my display adjustment?

Am using an Intel video driver with an i3 cpu. My System Settings says all drivers are correct. Are other drivers available somewhere to get my display settings back?

---

### Post by QIII on 2019-01-15
Before you work on possible driver issues (Intel graphics drivers are baked into the kernel, so there shouldn't be a problem), use the "rule-out" branch of diagnosis and eliminate a hardware fault in the monitor itself.  What you show there and your description of the behavior might indicate loose connections or a monitor that is about to spew blue smoke.

First check and double check the connections.

From that starting point, do the following the next couple of times this happens:

Either disconnect and reconnect the video cable or cycle the monitor power.

---

### Post by mrjacque on 2019-02-12
Problem was driver. for some reason, did not load with latest Ubuntu. Loaded old and works. 
See no reason why loose connection would keep driver from loading. Once the cable made connection, should be detected. Also, since never connected properly, the odds of a bad connection every boot is infinitesimal.,

---

### Post by SeijiSensei on 2019-02-12
When was the last time you ran "sudo apt update; sudo apt upgrade"?

---

