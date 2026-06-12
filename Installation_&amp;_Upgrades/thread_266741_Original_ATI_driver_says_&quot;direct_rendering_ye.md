---
title: "Original ATI driver says &quot;direct rendering: yes&quot;, fglrx driver says &quot;no&quot;?"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by OpticalIllusion on 2006-09-27
I have an ATI Mobility X300 and when I have the original Ubuntu driver, when I type in glxinfo it says 
```

direct rendering:  yes

```
When I go to ATIs website and download the newest Linux driver it says
```

direct rendering:  no

```

I'm trying to install and run XGL+Compiz and I read that if it says "no" then I can do it.  What's going on here?

---

### Post by OpticalIllusion on 2006-09-27
I guess no one knows.

---

### Post by jgeewax on 2006-11-07
I'm having a similar problem.

I have the fglrx drivers installed for Edgy (ATI Radeon 9800 Pro) and XGL and Beryl work great, but glxinfo | grep direct gives me a "direct rendering: no" response.

fglrxinfo gives me a bunch of info about my ATI card (and not stuff about Mesa as the guides say is a problem) yet direct rendering seems to be off. 

Anyone have solutions for fixing this?

JJG

---

