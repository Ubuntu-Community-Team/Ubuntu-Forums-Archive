---
title: "[SOLVED] Grub multiple entries"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2008-04-26
Hi,
After I upgraded to Ubuntu 8.10 I notice that on my grub menu I have this:

Ubuntu 8.04, kernel 2.6.24-16 generic
Ubuntu 8.04, kernel 2.6.24-16 generic(recovery mode)
Ubuntu 8.04, kernel 2.6.22-14 generic
Ubuntu 8.04, kernel 2.6.22-14 generic(recovery mode)

My question is why are there two extra entries?

I just click on the first one.

---

### Post by Pumalite on 2008-04-26
The first two are the kernels you are going to be working with. The next two is good to have them around in case you find yourself with no kernel to boot.

---

### Post by c007c on 2008-04-26
> **Rytron said:**
> Hi,
After I upgraded to Ubuntu 8.10 I notice that on my grub menu I have this:

Ubuntu 8.04, kernel 2.6.24-16 generic
Ubuntu 8.04, kernel 2.6.24-16 generic(recovery mode)
Ubuntu 8.04, kernel 2.6.22-14 generic
Ubuntu 8.04, kernel 2.6.22-14 generic(recovery mode)

My question is why are there two extra entries?

I just click on the first one.

Strange that the kernel used in 7.10 (2.6.22-14) was renamed as 8.04. I guess till your comfortable simply comment the "14" lines out.  

Once you feel comfortable with the migration use Synaptic package manager , search for 2.6.22-14, delete.

---

### Post by Rytron on 2008-04-27
Hi,
I know this thread is solved but here is a picture of my grub menu so that others with a similar situation can see.

---

