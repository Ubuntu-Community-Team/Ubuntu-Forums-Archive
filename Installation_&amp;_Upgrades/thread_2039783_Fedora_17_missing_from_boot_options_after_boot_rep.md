---
title: "Fedora 17 missing from boot options after boot repair"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by sid0972 on 2012-08-09
i installed fedora 17, yet another distro, it had a bootloader of its own, and it used to show every OS in the list
now i reinstalled grub2, cause i wanted to make windows as default OS, and now fedora is gone

what can i do to get it back in the boot options?

i tried boot repair again, but same thing

---

### Post by oldfred on 2012-08-09
Did you let Fedora use its default of a LVM?

In Ubuntu you need to add the lvm drivers and someone posted you still need to mount the Fedora partition to get the os-prober to see it.

sudo apt-get install lvm2
#mount the Fedora partition
sudo update-grub

---

### Post by sid0972 on 2012-08-09
yup, terminal shows it found fedora 17
thank you

---

### Post by oldfred on 2012-08-09
Glad that worked :)

---

