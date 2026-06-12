---
title: "gosh darned, infamous grub error 18"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by cdoublejj on 2010-02-18
i have an old Toshiba 2805 s202 i'm running with ubuntu jaunty aka 9.04. it's an older laptop and i just installed 160gb samsung hmc spin point. it's bigger than the bios supports so it can't find the kernel to boot. how do i got about setting it up on a full disk install? lvm says i can partions it an more partions and drives later but the thing is when you apt get it normally goes to the default partion. at least in the past.

maybe someone can elaborate for me. i did Google it but, i still feel a little lost. linux isn't a strong point yet, i'm still getting to know it pretty well. i did see lilo and looked up lvm.

just to clarify i got error 18 right after install.

---

### Post by kansasnoob on 2010-02-18
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

Simplest way I've found:

> Reduce the size of the Linux partition
One way of coping this problem which is reported to have worked for some people is to just try reducing the size of the Linux partition. (thus forcing the Linux kernel to be located be inside the limit). I have participated in one or two Ubuntu Web Forum threads where that seemed to solve the problem. A data partition can be used to fill the rest of the hard drive so it won't be wasted.
I have also read of three separate instances where users claimed that installing Linux '/' (root) on a logical partition instead of a primary partition cleared this problem up for them. (..."Go figure?"..!)

---

### Post by cdoublejj on 2010-02-21
Well i fixed it using the regular 9.04 cd, i was previously using the alt install. it did how ever cap the 160gb drive at 137gb, still better than nothing the latest bios for the toshiba satellite series is bios 2.0 last dated 03.

---

