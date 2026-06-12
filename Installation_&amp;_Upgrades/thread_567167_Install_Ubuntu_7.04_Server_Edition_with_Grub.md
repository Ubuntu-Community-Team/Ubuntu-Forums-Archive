---
title: "Install Ubuntu 7.04 Server Edition with Grub"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Scaryman on 2007-10-04
Hello,
when i install the  Ubuntu 7.04 Server Edition the installer instals always lilo, but i need grub. How can i change this?

Thanks.

---

### Post by briandu on 2007-10-04
Hi there,

once you login then do the following:

open terminal session

the type in:  sudo grub-install


it will prompt you for PWD and then that is it - say yes to the (hd0,0) in any event.

Reboot and voila!

---

### Post by Scaryman on 2007-10-04
When i do
"grub-install /dev/hda"

I became this:
"/dev/mapper/vgSDA-root does not have any corresponding BIOS drive."

---

