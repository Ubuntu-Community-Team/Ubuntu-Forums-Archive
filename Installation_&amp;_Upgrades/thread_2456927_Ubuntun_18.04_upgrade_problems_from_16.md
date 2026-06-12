---
title: "Ubuntun 18.04 upgrade problems from 16"
date: 2021-01-21
forum: Installation &amp; Upgrades
---

### Post by sapnabangalore191919 on 2021-01-21
We have recently upgraded our systems to 18.04 and the kernel changed to 4.15.0-132-generic #136-Ubuntu .It is giving problems with our software installed  also found that is not a stable release and its a debug kernel.We dont want a debug kernel
 things i need help

1)When will ubuntu release a stable kernel for this version?when we can expect and upgrade?whom should we contact?
2)how can we downgrade to 4.15.0-130-generic #134-Ubuntu ? I have checked in grub menu this kernel is not available.

Thanks

---

### Post by deadflowr on 2021-01-21
4.15.0-132 is (well was) a stable kernel.

How did you decide it was a debug kernel?


Anyway, likely moot as the current version is 4.15.0-134. Update your system and it should pull in the new kernel.

---

### Post by guiverc on 2021-01-21
You mention upgrading from 16 to 18.04.

Ubuntu has both releases that use *year.month *and different products that are *year* only.

An upgrade from Ubuntu Core 16 should ***not*** upgrade you to Ubuntu 18.04 LTS.  They are different products, and different systems (though they do share a common base).

I thus assume you meant a Ubuntu 16.04 LTS system that was upgraded to 18.04 LTS?

---

### Post by sapnabangalore191919 on 2021-01-22
Hi ,
Yes from Ubuntu 16.04 LTS system that was upgraded to 18.04 LTS.
Can you please brief why we should not upgrade from Ubuntu Core 16 should ***not*** upgrade you to Ubuntu 18.04 LTS.
Thanks

---

### Post by sapnabangalore191919 on 2021-01-22
When we check using dmesg command it shows debug kernel.

---

### Post by deadflowr on 2021-01-23
I don't see any debug output using the same kernel.
Can you post an example line or two of what it shows?

---

