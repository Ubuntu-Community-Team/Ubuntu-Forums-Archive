---
title: "Network connections - not saving changes?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by virtualu2 on 2009-09-29
I have tried adding a new static IP wired connection and just changing the default, no matter what it goes back to the default of DHCP?

---

### Post by robinl on 2009-09-30
I had the same problem too: in the end I did "sudo ifcconfig eth0 <ip>" to do it the old fashion way. Have you filed a bug?

---

### Post by LKjell on 2009-09-30
I think there is already a bug report [https://bugs.launchpad.net/network-manager/+bug/279384](https://bugs.launchpad.net/network-manager/+bug/279384)

Beside can't you set a static address on the router so it issue a static address to a spesific mac address?

---

### Post by jonandtice on 2009-09-30
> **LKjell said:**
> I think there is already a bug report [https://bugs.launchpad.net/network-manager/+bug/279384](https://bugs.launchpad.net/network-manager/+bug/279384)

Beside can't you set a static address on the router so it issue a static address to a spesific mac address?

I'm having the same issue.  That bug refers to not being able to asign an ip manualy and have dhcp assign dns and everything else.  My wireless card connects to the router and my wired card connects to my xbox.  My problem is I need to set my wired connection to a static ip and any changes made to that interface through Network Manager cause the connection editor to close and the changes aren't saved.

---

### Post by linux6994 on 2009-10-01
I am having the same issue with it not saving "Shared to other computers"
 Internet connection sharing not working in Alpha-6 now Beta (with updates)

---

### Post by bshosey on 2009-10-01
I am also having this problem as well

---

### Post by canabal on 2009-10-04
I am having the same problem, it is not saving, and network manager keeps crashing if I use the keyring (i.e. if I save it to all users.)

I just created a new bug report because the old one was not the same issue.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/442583](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/442583)

---

### Post by Loïc2 on 2009-10-05
This issue seems to have been reported already, see [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436109](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/436109). canabal, if the bug you reported is the same, could you please mark your bug as a duplicate?

---

### Post by gali98 on 2009-10-05
I have also filed a bug somewhat similar to this.
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/444068](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/444068)

I'm not quite sure if it would be considered a duplicate though...
Kory

---

### Post by gali98 on 2009-10-06
This is fixed, or at least my problem in the bug I filed is fixed. I assume the other problem has been fixed as well.
Kory

---

