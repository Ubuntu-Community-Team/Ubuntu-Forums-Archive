---
title: "Kernel, AUTOBUILD vs make-kpkg?"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by Griffy on 2007-09-26
Hi all,

Ubuntu Server 6.06, Dapper, kernel 2.6.15-29.60

I've been able to compile a new kernel without issues using the AUTOBUILD function (which works great), but I have not been able to figure out how to append my own version info to the images/debs. Is there a HowTo, or a  post somewhere that describes what needs to be changed in order to set custom version info using AUTOBUILD?


Question #2
I've attempted to build kernels the other way, using make-kpkg, and appending my own version and revision info accordingly, but I've had problems using that method. The kernel appears to compile fine, and my info is appended properly - however, none of those kernels ever work, they always result in a kernel panic on boot (keep in mind, its the same .config I used for AUTOBUILD, which works fine). Any suggestions on what may be missing or set improperly?

Thanks for any info, links, suggestions, etc.

Griffy

---

### Post by Griffy on 2007-09-27
Anyone?

---

### Post by Griffy on 2007-09-28
I find it hard to believe nobody has any idea on these questions....

Is there another more appropriate forum for them?

Thanks,

Griffy

---

### Post by timberXXX on 2007-10-05
For your Q2, How about use this method to build your new kernel?

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

