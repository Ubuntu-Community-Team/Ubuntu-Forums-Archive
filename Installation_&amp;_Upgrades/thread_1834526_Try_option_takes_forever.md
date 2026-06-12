---
title: "Try option takes forever"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by firefly431 on 2011-08-27
When I hit the try button, it just grays out the install button. The UI doesn't freeze, but I waited a long time with no reply. (I'm using old parts)

---

### Post by Mark Phelps on 2011-08-27
My own experience has been that 11.04 takes a terribly LONG time to boot ...

The Try Ubuntu option is loading a lot of stuff into system memory (since it can't write to the hard drive), and that taxex both CPU resources and system memory.

So, it is likely to take a very LONG time to boot.

When I first tried it, I nearly gave up myself, but eventually (after several MINUTES) it did finally get to a desktop.

---

### Post by Old_Grey_Wolf on 2011-08-27
> **firefly431 said:**
> When I hit the try button, it just grays out the install button. The UI doesn't freeze, but I waited a long time with no reply. (I'm using old parts)

What are the specs for the computer? You may be borderline on having enough RAM.

---

### Post by firefly431 on 2011-08-27
> **Old_Gray_Wolf said:**
> What are the specs for the computer? You may be borderline on having enough RAM.

Intel Pentium 4 CPU 3.00GHz 1.99 GB RAM (IDK what Physical Address Extension means)

---

### Post by firefly431 on 2011-09-04
Bump

---

### Post by gordintoronto on 2011-09-04
Video card?

---

### Post by Hakunka-Matata on 2011-09-05
> **firefly431 said:**
> Intel Pentium 4 CPU 3.00GHz 1.99 GB RAM (IDK what [COLOR=Red]Physical Address Extension means[/COLOR])

PAE extension adds the capability to address more than 2GiB RAM.  It is invoked automatically during install if RAM=>2GiB

What says ```
sudo lshw -C display
```

---

### Post by YannBuntu on 2011-09-05
> **firefly431 said:**
> When I hit the try button, it just grays out the install button. The UI doesn't freeze, but I waited a long time with no reply. (I'm using old parts)

Hello, 
I have the same problem on an old computer. To workaround this, I press a key at start-up when the 2 accessibility icons appear at the bottom of the screen, it displays the "old" boot menu (with Memory test and all..), then choose "Try Ubuntu without changing anything on the computer".

---

### Post by walt.smith1960 on 2011-09-05
Are you booting from a CD/DVD or USB?  I found a significant speed difference between 8 GB. USB sticks.  I have a Sandisk stick which certainly seems slower to boot than a CompUSA store brand. Both were created with the same version of Unetbootin.

---

### Post by Hakunka-Matata on 2011-09-05
> **walt.smith1960 said:**
> Are you booting from a CD/DVD or USB?  I found a significant speed difference between 8 GB. USB sticks.  I have a [COLOR=Red]Sandisk[/COLOR] stick which certainly seems slower to boot than a CompUSA store brand. Both were created with the same version of Unetbootin.

[http://ubuntuforums.org/showthread.php?t=1697175&highlight=sandisk](http://ubuntuforums.org/showthread.php?t=1697175&highlight=sandisk)

Look @ that thread, post# 4 in particular.
Also, I've read where some netbooks have a plastic piece installed in the sd card slot if your machine has one.  Not an actual sd card, but a piece of plastic to fill the hole.  It can screw up the install program, remove it and try your operation.

---

