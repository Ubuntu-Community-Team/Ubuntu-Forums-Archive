---
title: "linux-image 2.6.31-9 generic"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mosestruong on 2009-09-10
I've just upgraded to Karmic, and I can't boot using the new kernel, it hangs immediately after start up. 

Any ideas how I can get a log file to see what is causing the problem?

Thanks

---

### Post by xebian on 2009-09-10
> **mosestruong said:**
> I've just upgraded to Karmic, and I can't boot using the new kernel, it hangs immediately after start up. 

Any ideas how I can get a log file to see what is causing the problem?

Thanks

If you just did then you should have 31-10 not 31-9.

---

### Post by mosestruong on 2009-09-10
Well, I started the upgrade last night, but it didn't complete until this morning.

I'll do an update and see if it is fixed in -10.

---

### Post by executorvs on 2009-09-11
is it hanging in the GDM? if so this is a known bug.

---

### Post by swalker on 2009-09-11
acpi=off was needed here to not hang, way before it got to GDM, on an Inspiron 8500 with 2.6.31-10. 2.6.30-9 is the only kernel that hasn't hung for a while now iirc.

---

### Post by mosestruong on 2009-09-11
When I booted with the Recovery, it hung pretty early on, just after EDD Information not available... 

OK - so I guess this bug has already been reported? coz when I try searching for linux-image, i didn't think I see any that related to the kernel...

---

### Post by mosestruong on 2009-09-12
Thanks swalker, adding acpi=off worked for my old Compaq Presario 2800.

---

### Post by swalker on 2009-09-12
There's at least [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421244](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421244) that is seeing an ACPI issue with 2.6.31.

---

### Post by mosestruong on 2009-10-29
Thanks - the 2.6.31-14 kernel has resolved this issue now.

---

