---
title: "installing oracle in ubuntu vm"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by vaniub on 2010-04-26
Hello,
 
I have installed ubuntu in VMware player(Thank god! now i can switch between xp and ubuntu easily). 
 
Can i install Oracle in that now? 
 
One more question pls- Can i connect to this ubuntu from putty installed in other PC?
 
 
thanks
 
regds

---

### Post by P4man on 2010-04-26
> **vaniub said:**
> Hello,
 
I have installed ubuntu in VMware player(Thank god! now i can switch between xp and ubuntu easily). 
 
Can i install Oracle in that now? 

ahm, why not?
 > 
One more question pls- Can i connect to this ubuntu from putty installed in other PC?
 
Yes, but you will need to configure the networking in vmplayer. I dont know vmware, but in virtualbox I would set up NAT networking for one of the virtual NICs. I assume its the same for VMware. Then your ubuntu guest gets its own IP address and will be reachable on your network, just like it would be behind a nat router (windows host becomes the nat router).

---

