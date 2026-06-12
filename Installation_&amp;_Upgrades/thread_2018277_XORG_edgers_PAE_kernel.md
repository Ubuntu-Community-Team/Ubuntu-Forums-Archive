---
title: "XORG edgers PAE kernel?"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2012-07-06
Hi,

  Am I mistaken, or does Xorg Edgers PPA not include a PAE version of the kernel, just the 386 and the AMD64 versions?

Thanks,
CH

---

### Post by dino99 on 2012-07-06
Linus have dropped PAE

---

### Post by frogotronic on 2012-07-06
> **dino99 said:**
> Linus have dropped PAE

So...can one update from PAE to AMD64

- CH

---

### Post by dino99 on 2012-07-06
> **cement_head said:**
> So...can one update from PAE to AMD64

- CH

now "generic-pae" is renamed "generic" , so nothing to worry about  ):P

---

### Post by frogotronic on 2012-07-06
> **dino99 said:**
> now "generic-pae" is renamed "generic" , so nothing to worry about  ):P

Ok, so future kernel releases will upgrade PAE to generic, AND still address more than 2 GB of RAM?

Thanks & sorry for being dense.

- CH

---

### Post by wojox on 2012-07-06
> **cement_head said:**
> So...can one update from PAE to AMD64

- CH

Do you have the ability to run 64 bit?

---

### Post by frogotronic on 2012-07-06
> **wojox said:**
> Do you have the ability to run 64 bit?

yes

---

### Post by wojox on 2012-07-06
> **cement_head said:**
> yes

Why not just run 64 bit Ubuntu and not have to worry about PAE Kernels and such.

---

### Post by dino99 on 2012-07-06
> **wojox said:**
> Why not just run 64 bit Ubuntu and not have to worry about PAE Kernels and such.

because the future kernel will use 64 bits pointers AND 32 bits pointers fallback. That is how 3.5 works

so forget old garbage

---

