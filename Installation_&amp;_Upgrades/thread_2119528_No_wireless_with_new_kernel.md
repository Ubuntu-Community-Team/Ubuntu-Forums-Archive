---
title: "No wireless with new kernel"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by greythorne on 2013-02-24
Hello,

Just updated, when boot into the new kernel -3.5.0-25-generic i got no wireless. So went back to 3.5.0-17 and have wireless.

Any idea how to get wireless on the new kernel?

Thank you.

---

### Post by dino99 on 2013-02-24
the latest vanilla kernel is 3.8

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)


and you can get the others clicking on "parent directory"

---

### Post by fdrake on 2013-02-24
> **dino99 said:**
> the latest vanilla kernel is 3.8

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)


and you can get the others clicking on "parent directory"

that is not a stable kernle , still in apha development
wiki:[http://en.wikipedia.org/wiki/Software_versioning](http://en.wikipedia.org/wiki/Software_versioning)

for stable kernels use the kernel.org site:
[http://www.kernel.org/](http://www.kernel.org/)

if you have a fast inetrenet download the kernel(3.6.11) if not apply the corrisponding patch(3.5.7) to your kernel release. Remembre sometime compiling a kernel takes more time then the download.

---

### Post by fdrake on 2013-02-24
> **greythorne said:**
> Hello,

Just updated, when boot into the new kernel -3.5.0-25-generic i got no wireless. So went back to 3.5.0-17 and have wireless.

Any idea how to get wireless on the new kernel?

Thank you.
kernel 3.5.0 is still considered not stable you shoul at least have a kernel 3.5.x where x is at least >3 (final release).
also(it used to be ! ) remember that 3.y.x   => y = odd number = unstabble
                                     y = even number = stable.  
(now odd numbers are used for unstable version even if a y is odd it is considered stable for some reasons..)

so you should at least get kernel 3.6 (lettest on is 3.6.11 stick with it)

---

