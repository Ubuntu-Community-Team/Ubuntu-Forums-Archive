---
title: "I installed Kubuntu on my system"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by martindale_c on 2012-07-02
I installed Kubuntu on my system with Ubuntu and Window 7 on it. I got Kubuntu on it with a /media/60d0d0fc-6bbe-4d63-900e-1314f03449b1 on it  and I can not get on it. It displays the messege “You do not have the permissions necessary to view the contents of "60d0d0fc-6bbe-4d63-900e-1314f03449b1”. I got on my konsole and typed in sudo -i to get me a root sourse.  I then typed in/media/60d0d0fc-6bbe-4d63-900e-1314f03449b1. I don't know what to do next.

---

### Post by darkod on 2012-07-02
You mean you want to mount the Kubuntu partition into your Ubuntu installation? It sounds like that.

Kubuntu will have its own permissions and users, not sure if you can (and if you should) start touching it while running another OS.

If you want a common space for data, you should create a common data partition that all OSs can use.

---

### Post by martindale_c on 2012-07-02
[QUOTE=darkod;12070042]You mean you want to mount the Kubuntu partition into your Ubuntu installation? It sounds like that.

I already have mounted the Kubuntu partition. I want to know what the   60d0d0fc-6bbe-4d63-900e-1314f03449b1 is.

---

### Post by darkod on 2012-07-02
Sounds like that is the Kubuntu partition. The large combination of letters and numbers is the UUID code, a unique code each partition has.

You can view the UUID with:
sudo blkid

---

### Post by martindale_c on 2012-07-02
> **darkod said:**
> Sounds like that is the Kubuntu partition. The large combination of letters and numbers is the UUID code, a unique code each partition has.

You can view the UUID with:
sudo blkid

Thank you. That's what it was. 

Now I've got 750 GB that I can't find.

---

