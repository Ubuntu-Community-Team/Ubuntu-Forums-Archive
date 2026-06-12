---
title: "Is boot of window7 will be destroyed?"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by new7linux on 2011-06-10
hi guys:-

i had Win7 operating system only
 then i install Ubuntu 10.4,i became had dual boot(ubuntu,&Win7),,

if i install ubuntu 11.04  above Ubuntu 10.4, the boot of window7 will be lost?

---

### Post by Elfy on 2011-06-10
Assuming that you installed normally you would just end up with a triple boot. Does it not start with grub anyway?

---

### Post by new7linux on 2011-06-10
> **forestpiskie said:**
> Assuming that you installed normally you would just end up with a triple boot. Does it not start with grub anyway?

no i want remove ubuntu 10 , and install ubuntu 11"but i want still use win7"

---

### Post by Elfy on 2011-06-10
Did you install normally or did you install in Windows with wubi?

If you installed normally you can overwrite the existing install with the new one.

---

### Post by new7linux on 2011-06-10
> **forestpiskie said:**
> Did you install normally or did you install in Windows with wubi?

If you installed normally you can overwrite the existing install with the new one.

i not install yet,
 i asking before install,

ok, you say i can overwrite the existing"and windows7 will still work".

---

### Post by Elfy on 2011-06-10
> **new7linux said:**
> ok, you say i can overwrite the existing"and windows7 will still work"._If_ you installed normally - if you installed inside windows with wubi it's possibly a different story.

Run ```
sudo fdisk -l
``` from a terminal and post the results.

---

### Post by new7linux on 2011-06-10
> **forestpiskie said:**
> _If_ you installed normally - if you installed inside windows with wubi it's possibly a different story.

Run ```
sudo fdisk -l
``` from a terminal and post the results.

i [SIZE=4][COLOR=Red]not [/COLOR][/SIZE]want installed inside windows. 
i will installed normally, by press F12 at  start up  of computer   to " booting from DVD"

the run the code , the result:-

---

### Post by Elfy on 2011-06-11
Do the same again with the new cd or dvd - proceed with the install and when you reach the partition stage choose "Something Else" or "Advanced" - should be the last option.

Let the window refresh with the partition list - your existing install appears to be on sda4 - the only linux partition - so select that and click the Edit/Change partition button. In the new window that appears format and set the mountpoint to / save that and you'll be back to the partition list.

Carry on from there and it will install in the existing install.

---

### Post by westie457 on 2011-06-11
Hello, If you have installed programs and other personal files eg. music do not repeat do not tick the format box. 'forestpiskie' is correct in what he has stated above. His solution will give you a 100% clean install wiping out everything that was on the partition.

If you leave the format box unmarked the install will go ahead leaving your documents in place and upgrading any programs/packages that you installed in the previous version.

Hope this helps

---

### Post by new7linux on 2011-06-11
thank you guys i installed the new ubuntu..

---

