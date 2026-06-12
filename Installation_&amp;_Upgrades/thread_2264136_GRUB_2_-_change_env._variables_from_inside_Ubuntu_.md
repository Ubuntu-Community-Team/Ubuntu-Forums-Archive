---
title: "GRUB 2 - change env. variables from inside Ubuntu without resinstalling grub?"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by amaz1ng on 2015-02-05
Hi folks:

I'm experiencing basically exactly the same symptoms as this guy: [http://ubuntuforums.org/showthread.php?t=2164519](http://ubuntuforums.org/showthread.php?t=2164519)

With some small exceptions. I need to make the following changes in GRUB boot repair because I used gparted:

```

set prefix=(hd0,msdos6)/boot/grub
set root=(hd0,msdos6)
insmod linux
normal

```

But the problem is, I have to do this EVERY time I reboot my box. Can I change the GRUB environment variables from inside Ubuntu?

Thanks! :)

---

### Post by oldfred on 2015-02-05
Once booted just reinstall grub to MBR.

       sudo grub-install /dev/sda
sudo update-grub

If that does not work, run Boot-Repair and post the summary report.

---

### Post by amaz1ng on 2015-02-06
That worked. For the future:

[https://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](https://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

is also useful.

I couldn't figure out how to do it without reinstalling GRUB though.

---

