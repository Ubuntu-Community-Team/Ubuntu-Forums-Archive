---
title: "[SOLVED] Kernel 2.6.27-7 updated -&amp;gt; and the virtual terminals are gone"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by skkd.h4k1n9 on 2008-10-11
6 hours ago, before going to sleep I updated the system to kernel 2.6.27-7, now after booting up, I don't find my virtual terminals anymore, say, pressing [ctrl]-[alt]-[f1] to [ctrl]-[alt]-[f6] only ends up in a blinking cursor. I don't know, which automatically updated package caused this error, but I would be thankfully for any hint, how to get back the function fo virtual terminals.

Thanks in advance,

Karl

---

### Post by ktp on 2008-10-11
It's working here.

---

### Post by skkd.h4k1n9 on 2008-10-11
> **ktp said:**
> It's working here.

Wonderful, but the question was, if anybody has a solution to fix the error, and not to tell everyone, that someone doesn't have the problem :lolflag:

Testimonies are a wonderful thing, but not very helpful, sorry!

Karl

---

### Post by gtdaqua on 2008-10-11
> **skkd.h4k1n9 said:**
> 6 hours ago, before going to sleep I updated the system to kernel 2.6.27-7, now after booting up, I don't find my virtual terminals anymore, say, pressing [ctrl]-[alt]-[1] to [ctrl]-[alt]-[6] only ends up in a blinking cursor. I don't know, which automatically updated package caused this error, but I would be thankfully for any hint, how to get back the function fo virtual terminals.

Thanks in advance,

Karl

its ctrl+alt+f1.

---

### Post by skkd.h4k1n9 on 2008-10-11
> **gtdaqua said:**
> its ctrl+alt+f1.

Thanks for that help ... but that was only a missing typed 'f' followed by a copied version of [ctrl]-[alt]-[1] ... 

Karl

---

### Post by iponeverything on 2008-10-11
add vga=normal to your grub kernel boot options

---

### Post by incubus on 2008-10-11
Anything suspicious from

```

$ ls /dev/pts

```

or

```

$ ls /etc/event.d/tty*

```

?

---

### Post by skkd.h4k1n9 on 2008-10-11
```

$ ls /dev/pts

```

ls /dev/pts
0  1  2  3


```

$ ls /etc/event.d/tty*

```

ls /etc/event.d/tty*
/etc/event.d/tty1  /etc/event.d/tty3  /etc/event.d/tty5
/etc/event.d/tty2  /etc/event.d/tty4  /etc/event.d/tty6

---

### Post by hyperair on 2008-10-12
Run dmesg | grep uvesafb and see if it complains about v86d. if it does, then install v86d. This fixed the issue for me.

---

### Post by skkd.h4k1n9 on 2008-10-12
> **hyperair said:**
> Run dmesg | grep uvesafb and see if it complains about v86d. if it does, then install v86d. This fixed the issue for me.

Thanks a lot, Hyperair, that was the solution to the problem!

Kind regards,

Karl

---

### Post by hyperair on 2008-10-12
Glad to hear that.

---

### Post by asimon on 2008-10-12
Please, if something doesn't work, always make sure a bug is filed. Otherwise the mentioned solutions won't help all the people who don't happen to stumple across this thread.
In this case there is already [bug 273883: v86d missing from initramfs](https://bugs.launchpad.net/ubuntu/+source/v86d/+bug/273833). Thanks.

---

### Post by hyperair on 2008-10-12
I know there is already a bug filed. This workaround was taken from this bug: [https://bugs.launchpad.net/bugs/246269](https://bugs.launchpad.net/bugs/246269)

---

