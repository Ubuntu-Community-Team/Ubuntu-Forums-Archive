---
title: "what happened with my /dev/sda3 and 4?"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 2bob on 2009-10-08
Can somebody explain to me what happened with my /dev/sda3 and 4 please? Or at least to give me an idea where to read about this.
I have attached a screenshot with GParted and my system is Ubuntu Karmic, automatic install, use entire disc option.
Thank you!

---

### Post by kanikilu on 2009-10-08
Someone correct me if I'm wrong, but I think 3 and 4 are reserved for primary partitions (you can have up to 4 primary).

---

### Post by howefield on 2009-10-08
> **2bob said:**
> ....use entire disc option...

Isn't that where it went ?

In other words, a default install using that option will create two partitions on your disk. One for swap and one for everything else.

That's what you have got.

---

### Post by louieb on 2009-10-08
Don't worry - be happy. Thats the default way the Ubuntu installer creates partitions when doing a whole disk install.

In Linux - Primary and Extended partitions will always be shown as sda1,sda2,sda3 or  sda4. 
Logical partitions will always be sda5 and higher (sda5,sda6,sda7...)

As Gparted shows there is one of each: sda1-primary, sda2-extended,sda5-logical.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by 2bob on 2009-10-09
Good, good, good. Now I know to count better.:) Thank you very much!

---

