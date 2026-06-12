---
title: "Ubuntu Operating System version"
date: 2022-10-14
forum: Installation &amp; Upgrades
---

### Post by cgn1954 on 2022-10-14
Hi, new to this forum :-) but have been running Ubuntu for a few years now. My servers are used for simpler jobs like storage. 

I mostly use Webmin for Management, some SSH terminal too.  

My question: I have 2 Lenovo Lap Tops, one installed around 2019, the other installed this year (2022) but the older one "doesn't" come up in Ubuntu version 22, it stays at 20. What could be the reason? Shouldn't it "automatically" upgrade to version 22?

[IMG]https://www.cgn.se/v2/forumbilder/Ubuntu01.jpg[/IMG]

---

### Post by ActionParsnip on 2022-10-14
What are you using Webmin to do? The Ubuntu 20.04 release will not automatically upgrade to 22.04 but you can upgrade from 20.04 to 22.04 online.

---

### Post by Impavidus on 2022-10-14
No, it shouldn't automatically upgrade. You can run a release upgrade to get to 22.04. It usually works fine, but sometimes some applications need some reconfiguration or other fixing and on rare occasions it completely breaks your system.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

---

### Post by cgn1954 on 2022-10-14
Thank's - Webmin is very easy to use and supports my needs well, simple management. 

OK - then I will look to a proper way to upgrade...

---

### Post by ActionParsnip on 2022-10-14
```

sudo do-release-upgrade

```
Will upgrade the release. Note that if you want to work in Linux then webmin may not be available so learning common tools will give you transferable skills

---

