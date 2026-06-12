---
title: "ubuntu 6.06 on Virtual PC 2004SP1, network failed?!"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by tylau on 2006-06-02
I have got ubuntu installed in VirtualPC 2004SP1 running on XPSP! as host and the installation went fine on a virtual hard disk except have to use safe mode video on live CD bootup.  

Now the network is not working, I have try using static IP on eth0 and it still cant share the host IP, anyone got success in connecting to network?

Thanks. ](*,)

---

### Post by tylau on 2006-06-02
Magic bullet, setting Gateway DNS to 192.168.131.254 using DHCP on eth0 solved the problem, I am typing this on ubuntu 6.06 now. :D

---

