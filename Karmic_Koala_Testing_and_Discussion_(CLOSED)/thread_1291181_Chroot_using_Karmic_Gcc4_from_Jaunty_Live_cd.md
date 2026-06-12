---
title: "Chroot using Karmic Gcc4 from Jaunty Live cd"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-10-14
Hey, As the title says, how can i take control of the compiler in Karmic from a Jaunty live cd ? If it can be done at all.

Thanks.

---

### Post by VMC on 2009-10-14
Did you already try using chroot and cc or do you need to know how to choot? It appears you answered your own question by chrooting to  desired distro.

Edit: Maybe chroot [jail]("http://www.kegel.com/crosstool/current/doc/chroot-login-howto.html") is what your looking for.

---

### Post by Regenweald on 2009-10-14
> **VMC said:**
> Did you already try using chroot and cc or do you need to know how to choot? It appears you answered your own question by chrooting to  desired distro.

Edit: Maybe chroot [jail]("http://www.kegel.com/crosstool/current/doc/chroot-login-howto.html") is what your looking for.

Sorry, I already know how to chroot but was encountering problems when trying to install the binary driver for the chroot session. Obviously the compiler on the live cd and teh on in karmic needed to compile the binary are different. I was attempting to add the compiler to the chroot session and compile the driver.Did some reading up on jails but haven't quite gotten it yet.

I the meanwhile i have re-installed the open driver. 

Thanks for the response :)

---

