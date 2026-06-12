---
title: "error during installation"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Jkt610 on 2008-05-26
hi, after booting from the live cd, i click on install and heres what comes up...

[  xx.xxxxxx]ACPI:EC:acpi_ec_wait timeout, statuus=0,expect_event=1
[  xx.xxxxxx]ACPI:ECread timeout.command=128

I'm trying to dual boot vista/ubuntu. thanks.

---

### Post by iaculallad on 2008-05-26
> **Jkt610 said:**
> hi, after booting from the live cd, i click on install and heres what comes up...

[  xx.xxxxxx]ACPI:EC:acpi_ec_wait timeout, statuus=0,expect_event=1
[  xx.xxxxxx]ACPI:ECread timeout.command=128

I'm trying to dual boot vista/ubuntu. thanks.

Try hitting F6 on LiveCD boot and insert the **acpi=off** kernel parameter

---

### Post by Jkt610 on 2008-05-26
Thanks that solved it but I also have another problem now. I was trying to partition my drive using vista's partitioning tool. When I tried to shrink volume, it said I could only partition the drive by about 8 gigs when my drive has about 50 gb left. Why is it doing this? i tried defraging the drive once but that didn't do anything.

---

### Post by iaculallad on 2008-05-26
> **Jkt610 said:**
> Thanks that solved it but I also have another problem now. I was trying to partition my drive using vista's partitioning tool. When I tried to shrink volume, it said I could only partition the drive by about 8 gigs when my drive has about 50 gb left. Why is it doing this? i tried defraging the drive once but that didn't do anything.

Better use [GParted]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") to shrink vi$ta's partition for you.

Note: Defrag your vi$ta partition first before Gpart'ing.

---

### Post by Jkt610 on 2008-05-26
I've seen this trick before but that problem is that I don't have a Vista installation cd/dvd at the moment which the guide you linked to above says you need to have. Is there an alternative way to partition my drive or is this the only way?

---

### Post by iaculallad on 2008-05-26
> **Jkt610 said:**
> I've seen this trick before but that problem is that I don't have a Vista installation cd/dvd at the moment. Is there an alternative way to partition my drive or is this the only way?

To partition you're drive, you could always use the Partition Manager that comes along with your Ubuntu LiveCD. That's the best there is.

---

### Post by Jkt610 on 2008-05-26
Ok I will try this tommorrow. Thanks for all ur help.

---

