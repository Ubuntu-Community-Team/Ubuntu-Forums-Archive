---
title: "Upgrading via a fresh install while keeping home partition"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by WebDrake on 2008-10-24
Hello all,

Normally when I upgrade my (K)ubuntu version I just do a fresh install, while leaving my /home partition untouched.

In this case I'm not sure if this is appropriate, given the KDE3-->4 transition.  How will the system deal with my .kde directory?

Thanks in advance,

   -- Joe

---

### Post by philinux on 2008-10-24
As before you **dont** tick the box to format home so no worries.

---

### Post by WebDrake on 2008-10-24
> **philinux said:**
> As before you **dont** tick the box to format home so no worries.
Well, that goes without saying. :-)

... but as a tester can you confirm that the new Ibex install will deal OK with the .kde directory?

---

### Post by surfed on 2008-10-24
I have kept my home partition over many installs of even different distros, and have encountered few issues, currently did a switch from hardy to intrepid and the only thing i am carfull about is installing all the packages needed before mounting home. Like that if you have lets say a certain compiz setting that depends on a non default package it will not get changed by compiz. Just leave your /home partion alone during install and add entry to fstab later. Just make sure you use the same username.

---

### Post by panda726 on 2008-10-24
That is an interesting point you make Surfed.  I am soon going to be doing this type of upgrade on two machines, one Hardy, and the more important one Gutsy.  This applies to "accessories" to auto-loaded things only?  I suppose the nvidia driver for my dual monitor would apply though.

Tor

---

