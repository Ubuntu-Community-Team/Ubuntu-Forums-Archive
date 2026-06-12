---
title: "Network devices disabled"
date: 2010-01-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Waelwulf on 2010-01-26
've been running the Lucid Lynx alpha since first release and only now, after recently putting my computer into suspend then restarting, has the networking failed completely.

Both wireless and ethernet list as disabled with sudo lshw -C network. The wireless adapter is an Atheros AR928X. The ethernet is a Realtek RTL8111/8168B.

Any suggestions as to how I might go about fixing this?

---

### Post by philinux on 2010-01-26
> **Waelwulf said:**
> 've been running the Lucid Lynx alpha since first release and only now, after recently putting my computer into suspend then restarting, has the networking failed completely.

Both wireless and ethernet list as disabled with sudo lshw -C network. The wireless adapter is an Atheros AR928X. The ethernet is a Realtek RTL8111/8168B.

Any suggestions as to how I might go about fixing this?

I had this except I had no connections listed under wired. I had to go to edit connections click add and take the defaults and click apply.

---

### Post by Waelwulf on 2010-01-26
> **philinux said:**
> I had this except I had no connections listed under wired. I had to go to edit connections click add and take the defaults and click apply.

I had an "Auto eth0" connection listed. I deleted this, made a new wired connection and took defaults but I still have zero connectivity.

---

### Post by Waelwulf on 2010-01-27
I solved this issue by adding the lines 
```
auto eth0
iface eth0 inet dhcp
```
to my
```
/etc/network/interfaces
```

Only my loopback interface was listed in the file before editing.

---

