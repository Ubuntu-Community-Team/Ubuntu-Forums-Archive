---
title: "ICS connection sharing alpha-6 isn't working"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by linux6994 on 2009-09-30
I just did a clean install of Alpha-6 and the only thing I can see wrong so far is that when I try to set my eth0 to "Shared to other computers" this settings does not stay, the GUI closes and auto dhcp is set once again.

---

### Post by linux6994 on 2009-09-30
same problem as NETWORK MANAGER NOT SAVING CHANGES.

---

### Post by jonandtice on 2009-09-30
Same problem here.  My wireless connection is working but any changes I make to my wired connection cause the connection editor to close and the changes aren't applied.  The problem occurs with any type of change to eth0, not just the ICS setting.

I have ICS working now through firestarter.  If you can't wait for Network Manager to be fixed try:

```
sudo apt-get install firestarter
```
```
sudo ifconfig eth0 *ip*
```
assuming eth0 is the interface you want to share. ip is an ip address ex. 192.168.0.1
Then use firestarter to share your connection.

---

### Post by linux6994 on 2009-09-30
Its showing that my eth0 is not ready.

---

### Post by Eestlane on 2009-09-30
Try
```
sudo apt-get install dnsmasq-base
```
If it wasn't installed it was most probably the issue.

---

### Post by linux6994 on 2009-09-30
dnsmasq-base is already the newest version.

---

