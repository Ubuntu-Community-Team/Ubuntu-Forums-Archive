---
title: "ubuntu 20.04 logoff to a black screen"
date: 2020-10-13
forum: Installation &amp; Upgrades
---

### Post by khbehrens on 2020-10-13
Memory: 31.0 GB, Processor: Intel Core i5-6500 CPU 3.2 GHz, Graphics Mesa Intel HD Graphics 530 (SKL GT2), dual monitors joined displays, resolution 1920x1080 (16:9) connected via DVI.
I upgraded from 18.04 LTS to 20.04 LTS. When I logoff I get a blank screen with a blinking cursor. The only way to get the machine to work is to reboot. This issue did not occur in 18.04.
Lock screen works with a logon screen displayed.
I can find no reason why this is happening and I am looking for any possible solution that the community may suggest.

---

### Post by khbehrens on 2020-10-31
I found that /etc/gdm3/PostSession/default had this line:
sleep 0.9
The logout problem was fixed when I commented this line out.

---

