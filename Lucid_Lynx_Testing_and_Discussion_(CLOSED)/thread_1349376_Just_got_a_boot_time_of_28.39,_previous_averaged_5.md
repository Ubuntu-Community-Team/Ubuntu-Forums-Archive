---
title: "Just got a boot time of 28.39, previous averaged 58 seconds."
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-12-08
Usplash logo is mangled and the sound is muted at the desktop but wow, what a fast boot.

---

### Post by VMC on 2009-12-08
Same here, but since xsplash is disabled for the time being, I think its a bogus boot. Wait until they re-enable whatever splashes for the final to see the real boot times. 

I'm wondering if some needed services are also missing.

---

### Post by philinux on 2009-12-08
Step in the right direction though eh. ;)

---

### Post by LKjell on 2009-12-08
You can enable xplash by uncomment in /etc/gdm/Init/Default  and /etc/gdm/PreSession

In Init
```
if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi

```

In PreSession
```
if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --daemon
fi

```

---

### Post by andrewabc on 2009-12-08
Is this timed watch from grub to desktop or what? bootchart?

---

### Post by philinux on 2009-12-08
> **andrewabc said:**
> Is this timed watch from grub to desktop or what? bootchart?

Bootchart but timed as well. Times match.

From grub to usable desktop.

---

### Post by andrewabc on 2009-12-08
> **philinux said:**
> Bootchart but timed as well. Times match.

From grub to usable desktop.

So they switched bootchart to not add the extra 45 second delay? Otherwise there is no reason for them to match unless your computer is very old.

My 9.10 bootchart is 51 seconds, but at usable desktop in 11.

---

### Post by philinux on 2009-12-08
> **andrewabc said:**
> So they switched bootchart to not add the extra 45 second delay? Otherwise there is no reason for them to match unless your computer is very old.

My 9.10 bootchart is 51 seconds, but at usable desktop in 11.

Last boot was back to 52 seconds on bootchart. It seemed like that from the wall clock too.

Amd x64 5100+ 2gig mem. Pc 18 months old.

---

### Post by vishalrao on 2009-12-09
From the desktop meeting email, xplash saved about 0.8 seconds so its still pretty good... I cant wait to get back home from travel to get on Lucid...

---

### Post by philinux on 2009-12-09
Just rebooted this morning and back to 28 seconds. Timed from wall clock.

Usplash logo still mangled and sound muted. Bootchart attached if anyone interested.

---

