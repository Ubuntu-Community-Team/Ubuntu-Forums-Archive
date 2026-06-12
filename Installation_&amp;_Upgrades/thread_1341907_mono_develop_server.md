---
title: "mono develop server"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by narayanank84 on 2009-11-30
i have installed mono develop in my system which has got ubuntu jaunty on it. i am not able to run my aspx files,it says i need to install xsp2 server,how do i install that .if not what alternate solutions do i  have.

---

### Post by Dragonbite on 2009-11-30
> **narayanank84 said:**
> i have installed mono develop in my system which has got ubuntu jaunty on it. i am not able to run my aspx files,it says i need to install xsp2 server,how do i install that .if not what alternate solutions do i  have.

You can either install XSP, which is a smaller, local web server, or the full-blown apache + mod_mono so you can run a local web server that will run Mono-based ASP.NET applications.

You should be able to find XSP in Synaptic. If not, then look under "mono-xsp" which it may be listed as.

---

