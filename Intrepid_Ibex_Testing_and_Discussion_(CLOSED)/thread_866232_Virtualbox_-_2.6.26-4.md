---
title: "Virtualbox - 2.6.26-4"
date: 2008-07-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by andrek on 2008-07-21
Hey, just because there are still no virtualbox-ose-modules package for a current Intrepid's kernel, virtualbox seems unusable and useless at all. Is there any information when will be needed package released?

and oh, don't tell me to try moving back to 2.6.26-3 kernel - my nvidia drivers don't work with it at all.

---

### Post by MacUntu on 2008-07-21
2.6.26-2 works for me but I guess you can't go back without a working kernel. :-/

---

### Post by dinxter on 2008-07-21
installing the 6.2 ubuntu package from the virtualbox/sun website will compile its own kernel modules and work happily on intrepid until the ubuntu repository version for 2.26.6-4 is available, its what im using just now

---

### Post by andrek on 2008-07-21
> **dinxter said:**
> installing the 6.2 ubuntu package from the virtualbox/sun website will compile its own kernel modules and work happily on intrepid until the ubuntu repository version for 2.26.6-4 is available, its what im using just now

Thanks alot. I will try it now.

---

### Post by Quikee on 2008-07-21
Hm... you have the source available in the repository under virtual-box-source. With module-assistant and the source you can create the module package for a newer release by yourself and easily (only "sudo m-a a-i virtualbox-ose" is needed I think). 

I bet in the future it will be done just in this way but automated via DKMS - at least that is how they have done it for nvidia modules.

---

### Post by alkamid on 2008-08-19
Hello

How can I download the 1.6.2 version of Virtualbox? On sun/virtualbox website I can only get the 1.6.4

---

