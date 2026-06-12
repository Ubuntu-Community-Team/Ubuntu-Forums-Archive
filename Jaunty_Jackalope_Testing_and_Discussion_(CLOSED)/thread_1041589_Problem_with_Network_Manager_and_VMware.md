---
title: "Problem with Network Manager and VMware"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlward4th on 2009-01-16
I'm using the latest NetworkManager in Ubuntu Jaunty and having a problem related to VMWare.  VMWare creates two network devices by default (vmnet1 & vmnet8 ).  NM thinks that these are wired devices and that it needs to manage.  So I get:

Wired Network vmnet1
 * Auto vmnet1


But these devices really shouldn't be managed by NM and this causes routing problems because NM uses vmnet1 for my default route.

I used to deal with this problem by just removing "Auto vmnet1" and "Auto vmnet8" every time my computer boots.  But now when I try to remove those devices I get an error:

Removing connection failed: nm-settings.c.333 - Read-only connections may not be deleted..


Any idea how I can deal with this problem?  Thanks!

-James

---

### Post by ayates on 2009-01-16
I had the same problem. For now, since I'm only wired, I removed NM and set up /etc/network/interfaces the old way.

---

### Post by LordVeovis on 2009-01-16
I had a problem with network manager wanting to assign my nics that I assigned to a bond.  I was able to disable the auto assigning:

/etc/network/interfaces
```

auto eth0
iface eth0 inet manual
auto eth1
iface eth1 inet manual

```

so if you add this (replace eth0 and eth1 with the names) it should not try.

---

### Post by LordVeovis on 2009-01-16
So like this:
/etc/network/interfaces
```

auto vmnet1
iface vmnet1 inet manual
auto vmnet8
iface vmnet8 inet manual

```

---

### Post by ayates on 2009-01-16
I tried LordVeovis' solution  and it also works.

---

