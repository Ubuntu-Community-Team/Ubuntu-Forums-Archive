---
title: "Kernel Downgrade"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by bidkar on 2008-06-04
Hi All,
      Please help me in downgrading my kernel for Ubuntu8.04 version.
Here is the scenario:
Currently I have ubuntu8.04, with kernel version 2.6.24-18.
I need kernel version 2.6.18 or 2.6.19 for my current project. Is it possible to downgrade the kernel for ubuntu 8.04? if possible how?

Thanks,
Bidkar

---

### Post by rpw on 2008-06-04
First I have to say: be very, very carefull with the way I will mention here! So please make a backup before you do this!

I had (and still have) problems with the hardy kernels, I'm getting some error messages when I try to play a video DVD.

So I included the gutsy repo (deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main multiverse restricted universe) to my hardy installation and installed the latest gutsy kernel.

After this I disabled this repo again, and everything now works fine.

Regards,

rpw

---

