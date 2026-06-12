---
title: "Ubuntu7.10 on MSI GX700-046 == ACPI problems :S"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by pokemon_jojo on 2008-02-09
Hi all,

I have buy a MSI GX700-046. I have install ubuntu 7.10 without any problem during install.

Nearly all work, but i have a big problem with ACPI i think.

I have try this solution : [https://wiki.ubuntu.com/LaptopTestingTeam/MSIMegabookGX700](https://wiki.ubuntu.com/LaptopTestingTeam/MSIMegabookGX700)

but don't work !

Is there a way to fix this problem ? If somebody have idea (or good link).

Thanks in advance

---

### Post by Partyboi2 on 2008-02-09
So you tried using noacpi boot argurment?

---

### Post by Koba on 2008-02-09
I figured I was like the only person in the world with ubuntu on a GX700 :P I'm glad I saw this topic, I was wondering about the ACPI too.

---

### Post by impact on 2008-02-10
You are definitely not the only GX700 + Ubuntu user. However, since MSI doesn't support Linux and doesn't provide a Linux-compatible BIOS, there are some problems, mostly with the power management.


[http://bugzilla.kernel.org/show_bug.cgi?id=9823](http://bugzilla.kernel.org/show_bug.cgi?id=9823)

---

### Post by pokemon_jojo on 2008-02-11
> **Partyboi2 said:**
> So you tried using noacpi boot argurment?

Yep, and it does nothing :(

noacpi boot argument work for you ?

---

### Post by pokemon_jojo on 2008-03-16
I have found pseudo solution ;)

replace "noacpi" by" acpi=off"

---

