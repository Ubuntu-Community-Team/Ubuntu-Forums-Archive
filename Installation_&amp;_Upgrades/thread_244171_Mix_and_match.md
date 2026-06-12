---
title: "Mix and match?"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by Toehead on 2006-08-26
Breezy recognizes my on board ethernet perfectly, whereas dapper does not. I cannot get the internet working with dapper. Is it possible to retain the code for my card from breezy, and upgrade evertything else to dapper? The new release is very nice, and I would like to be able to upgrade:
Here are the specs:
Compaq armada 6500 laptop (got for free)
300 MHZ 
thats about it. 

Thanks for your help in advance.
Regards
-Brendan

---

### Post by aysiu on 2006-08-26
Mixing and matching is a really bad idea and will leave you with a broken. Stick with Breezy and file a bug report.

---

### Post by Ptero-4 on 2006-08-26
toehead. The problem with Dapper is that kernels 2.6.14 and later (I know this b/c I just compiled a vanilla 2.6.14 in breezy and got the same errors I get on a vanilla Dapper install) seems to have some missing parts (which happens to be necesary to allow RAW reading undetected hardware modems) and cannot use a hardware modem if it needs to be set manually (i.e: pppconfig cannot detect it).

---

### Post by Toehead on 2006-08-28
Any workaround, or word when a fix will be released?

---

### Post by aysiu on 2006-08-28
A fix won't be released until they know about the problem. File a bug report:
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by Toehead on 2006-08-29
Done :) Thanks, hopefully this gets resolved.

---

### Post by PPAAUULL on 2006-08-29
I have no Idea why it wouldn't find it. I was helping on of my friends install linux on a similar computer and it picked it up just fine. hmmm.

Paul

---

### Post by Toehead on 2006-08-29
> **PPAAUULL said:**
> I have no Idea why it wouldn't find it. I was helping on of my friends install linux on a similar computer and it picked it up just fine. hmmm.

Paul

I have no idea either. It wouldnt find it, twice. I tried a second time to be sure. Then, my bud who has been running breezy on the same computer for a while upgraded and got the same results.

---

### Post by Ptero-4 on 2006-08-31
> **aysiu said:**
> A fix won't be released until they know about the problem. File a bug report:
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Done already. Nobody seems to read it though.

---

