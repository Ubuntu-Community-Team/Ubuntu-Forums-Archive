---
title: "Disable the Firewall"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by dgore on 2007-03-06
New to Ubuntu.  Is there a firewall in Ubunta.  If so I want to turn it off.  I have a hardware firewall and don't need it.  Can someone give me instructions to do this?

Thanks,

---

### Post by TheWizzard on 2007-03-06
you can get rid of all the firewall rules with:
sudo iptables -F

---

### Post by Malakia on 2007-03-06
Actually in Ubuntu you don't necessarily have a firewall. By default all the ports are closed and as you need them they open.

---

### Post by Ek0nomik on 2007-03-06
Thanks for that little tidbit of info Malakia.  :)

---

