---
title: "No support for amd/ati radeon proprietary drivers"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by chowse on 2016-04-25
Hi,
Just a tiny bit confused.  I've read the articles about no proprietary AMD drivers in 16.04.
I have an [AMD/ATI]: Cedar [Radeon HD 5000/6000/7350/8350 Series] video card, but Software & Updates / Additional Drivers tells me "No proprietary drivers are in use."
I'm using the X.Org X server driver. (Open source and tested.)  Happy with it for what I do.

Seems to me like it would be OK to upgrade, yes??

Thanks,
Charles

---

### Post by EmpireITtech on 2016-04-25
Have you gone through some of this documentation? [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by QIII on 2016-04-25
If you are sure you have no graphics driver installed, then when you upgrade either Radeon or AMDGPU will be installed depending on your chipset.

---

### Post by chowse on 2016-04-25
With great respect EmpireITtech, the recommended documentation is over my head technically.  I'll be happy to post the results of any terminal commands if you like.
Here's one from the doc page...

charles@MOE:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] [1002:68f9]


QIII, so they're both open source, so I'd be no better or worse off, yes?

---

