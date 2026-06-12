---
title: "apt-get install not working on Ubuntu 7.10"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by tejasrsuthar on 2007-12-04
hi, fro

---

### Post by fazavon on 2007-12-04
There are really only two reasons that it will not work.

1. You will need to add sudo to the line, it should read sudo apt-get install package name, or you can set up an alias to auto fill the sudo apt-get part.

B. You are sitting behind a proxy and you need to set you network Proxy along with your browser proxy. this can be done from System> Preferences> Network Proxy.

Of course these are both contingent on you have a network connection at all.

thanks

//j

---

### Post by tech9 on 2007-12-04
> **fazavon said:**
> There are really only two reasons that it will not work.

1. You will need to add sudo to the line, it should read sudo apt-get install package name, or you can set up an alias to auto fill the sudo apt-get part.

B. You are sitting behind a proxy and you need to set you network Proxy along with your browser proxy. this can be done from System> Preferences> Network Proxy.

Of course these are both contingent on you have a network connection at all.

thanks

//j

if your behind a proxy. it's a little more complicated than just inputting your proxy url in System> Preferences> Network Proxy.
look into ntlmaps

---

### Post by fazavon on 2007-12-05
Not really, we run a proxy at work, and all I have ever had to do is add the network proxy.... and knees to the sky.

---

