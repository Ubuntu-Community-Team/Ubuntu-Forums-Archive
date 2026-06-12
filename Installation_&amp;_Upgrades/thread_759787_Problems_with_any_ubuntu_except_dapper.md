---
title: "Problems with any ubuntu except dapper"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by daniel8 on 2008-04-19
Hey all, iv installed ubuntu like a month ago
and after trying many versions of ubuntu, the only one that seems to work is the dapper drake
Iv noticed that in the others (iv tried 7.10 and 8.04) the net doesnt work as it is supposed to
for example, when i try to surf the net, it takes loads of time loading any page, or doesnt load them at all.
the internet works, and the router is well configurated (it works fine in the other 2 machines) in fact iv tried IRC and it works fine, seems like it is just the HTTP protocol(altho aMSN doesnt connect)
this is kinda weird but iv also tried Mandriva 2007 and Mandriva 2008 as well as Ubuntu 7.10 n 8.04.
The pc is running on a INTEL cpu dual core 1.8 E2160
Motherboard asus P5GC-MX video card integrated.
1gb ram ddr2. thats it.
if you could give me any hints else im just sticking with dapper
:lolflag:
Thanks in advance!

---

### Post by wpshooter on 2008-04-19
Are you installing these other versions to a hard drive or are you running it off of a live CD ?

---

### Post by daniel8 on 2008-04-19
No no iv tried them from the live cd first then installed them thought maybe with the full installation it would auto-fix with updates or something
but apparently it didnt.

---

### Post by Maintech on 2008-04-19
just out of curiosity, have you tried any boot option? Noapic, pci=nomsi, etc? Sometimes the new motherboards have issues.

---

### Post by daniel8 on 2008-04-20
Hm no i haven't hmm i dont even know what it is

---

### Post by Partyboi2 on 2008-04-20
You could try disabling IPv6 in firefox and seeing what happens.
open up firefox and in the address bar type
```
about:config
``` then look for this
```
network.dns.disableIPv6
```then double click on it to change it to true.
Or to disable IPv6 over your whole system open a terminal (Applications>Accessories>Terminal) and type
```
echo "blacklist ipv6" | sudo tee -a /etc/modprobe.d/blacklist
```
then restart


---

