---
title: "Latest kernel wont boot - previous one will. Error enclosed."
date: 2008-07-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-07-10
Any ideas or just wait for another kernel.

---

### Post by Nullack on 2008-07-10
Kernel panics usually require code changes so waiting is in order imho

---

### Post by philinux on 2008-07-10
Ok will sit tight with tin hat on :lolflag:

---

### Post by plun on 2008-07-10
> **philinux said:**
> Any ideas or just wait for another kernel.

Well...the famous dist-upgrade discussion again....[-X


There was a ABI bump version for the kernel on Monday/Tuesday I think....

Do you have it...?


Post the output of this if you are unsure

```

sudo apt-get update && sudo apt-get dist-upgrade
```


EDIT

Forgot most important... start in **recovery mode**... I was stucked there..



:)

---

### Post by plun on 2008-07-10
Followup about this...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243933)


Maybe a stone dead install if dont have other kernels.:(

To chroot a VB install is also maybe too much...maybe it works:confused:

But test recovery !  (other kernels installed ? )

---

### Post by philinux on 2008-07-10
I've killed the vbox and gonna wait for the alpha 2 and install it on my second HD.

---

