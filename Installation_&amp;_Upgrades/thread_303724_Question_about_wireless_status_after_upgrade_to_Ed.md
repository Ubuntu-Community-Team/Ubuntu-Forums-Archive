---
title: "Question about wireless status after upgrade to Edgy"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by HokeyFry on 2006-11-20
okay not sure if this would belong in wireless or in upgrades but w/e if it bothers anyone then move it


are there issues with ndiswrapper when upgrading to edgy? and if so, would it be a problem since I already compiled ndiswrapper from source instead of using the ubuntu repositories?

---

### Post by Dr. Nick on 2006-11-20
If you compiled it from source you will need to recompile it, you most likely compiled it against the running dapper kernel and that most likely will not work with the new edgy kernel. 

The ubuntu repos I believe are built against the proper kernel, you could either install the ubuntu ver or recompile it from source against the new kernel if it doesnt work

---

