---
title: "LVM users beware linux_2.6.31-7.27-generic"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2009-08-25
A warning from one of the Ubuntu developers on [identi.ca]("http://identi.ca")
> 
@crimsun: #karmic encrypted lvm users should avoid linux_2.6.31-7.27-generic - cryptsetup fails to mount /, so boot will spin indefinitely

---

### Post by dino99 on 2009-08-25
i've seen this too when installing 31-7-generic

---

### Post by crimsun on 2009-08-25
Symptom is being tracked as [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/418514](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/418514) (LP seems to be experiencing issues ATM)

---

### Post by Technoviking on 2009-08-25
> **crimsun said:**
> Symptom is being tracked as [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/418514](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/418514) (LP seems to be experiencing issues ATM)

Thanks for the update.

T-V

---

### Post by Jim March on 2009-08-25
Yup.  NO joy whatsoever here.  I used the Karmic64 Alpha4 alt-installer to do whole disk encryption on Ext4.  The -7 kernel blows it the hell up.

---

