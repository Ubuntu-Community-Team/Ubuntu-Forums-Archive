---
title: "NFS mount with Intrepid"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nickzeff on 2008-10-10
Hi,

Upgraded to Intrepid this week, and most things are ok except for two things:

1. Annoying flashing wireless LED
2. NFS mount not automatically mounting

(1) I can live with, but (2) is quite inconvenient.

I have the following in the /etc/fstab

```
my-server-name:/media/alpha /media/shared nfs rw,user 0 0
```

and this was enough to automatically mount my local /media/shared dir to a network NFS share on startup in Hardy.

However, Intrepid requires a manual mount command following startup. Doing a **mount /media/shared** works with no problems.

Is it because the share is not available until network manager sorts itself out and connects? I'm not sure, since this seems to happen when I'm both wired and wireless at startup.

All suggestions gratefully received.

Cheers

N

---

### Post by nickzeff on 2008-10-10
*bump*!

---

### Post by exactopposite on 2008-10-15
I'm having the same problem in kubuntu intrepid. I can manually mount my nfs shares, but they don't automount on startup from fstab

---

### Post by exactopposite on 2008-10-21
> **exactopposite said:**
> I'm having the same problem in kubuntu intrepid. I can manually mount my nfs shares, but they don't automount on startup from fstab

I reinstalled kubuntu intrepid beta this morning, and nfs is working properly. I'm not sure what caused the problem with the previous install.

---

### Post by expatCM on 2008-10-23
I also have this problem on one client machine.  There are three other clients on the network and they all work without issue.  So I am looking for what is different.

Manually mounting the shares works without any problems (mount -a).

The only thing I have noticed is that on the problem machine there are two nics.  One is part of the motherboard and not used, it is defective.  So I am wondering if it is that there are two cards on the machine that is influencing this .....  Still need to find time to explore a bit more.

I have also noticed that CUPS is not finding the printers on the server.  I guess there is a connection here but until I know my mind is open ....

---

