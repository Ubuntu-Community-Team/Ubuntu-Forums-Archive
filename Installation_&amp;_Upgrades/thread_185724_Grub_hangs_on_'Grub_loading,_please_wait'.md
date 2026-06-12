---
title: "Grub hangs on 'Grub loading, please wait'"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by dendenners on 2006-06-01
Hi,
I'm new to Ubuntu (been using gentoo for years though) and I'm trying to do my first install (using the server iso). The install seemed to go fine in general. I'm using a boot partition (/dev/sda1). However on boot the system hangs on 'Grub loading, please wait...'. I went into the system in rescue mode and took a look at the files in /boot. There are the usual boot related files, but there's no grub.conf. Is this a feature of Ubuntu, or am I missing something?
Thanks
Denis

---

### Post by dendenners on 2006-06-01
Sorted it - Raid was switched on in the bios and ubuntu was installed on the first volume. Once I switched raid off it worked.

---

### Post by marshal on 2008-06-17
thx, old post, but helped me very much =)

---

