---
title: "new kernel?"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-10-11
I see references to a new karmic kernel, 2.6.31.13? I'm only at 2.6.31.12 with all the latest updates. Am I missing something, should there be a new kernel?

---

### Post by Darkshade on 2009-10-11
Make sure your mirror is up to date or switch to the main server if you want the latest updates at time :)

---

### Post by jppr on 2009-10-11
yes, when you update your system you have latest 2.6.31-13.44 kernel :popcorn:

---

### Post by GeorgeVita on 2009-10-11
> **jppr said:**
> yes, when you update your system you have latest 2.6.31-13.44 kernel :popcorn:

and for your safety KEEP your older kernels to come back!

**2.6.31-11** is a 'good' one!

---

### Post by oboedad55 on 2009-10-11
Thanks for the replies. I'll change my mirror. I think I've been using one at Duke University in north carolina.

---

### Post by GeorgeVita on 2009-10-11
Just for the history:
> **oboedad55 said:**
> I just updated karmic and got the new .13 kernel. Upon bootup the system hung on a black screen after the white ubuntu logo passed. I mean, it's completely black, no way to input anything. Any ideas? I'm posting this using the previous kernel.

---

### Post by oboedad55 on 2009-10-11
> **GeorgeVita said:**
> Just for the history:

Thanks for posting that. I'm glad I keep older kernels.

---

### Post by dentaku65 on 2009-10-11
This is a grub issue (or wrong package installed).
I solved in this way:
```
sudo apt-get install grub2
```

---

