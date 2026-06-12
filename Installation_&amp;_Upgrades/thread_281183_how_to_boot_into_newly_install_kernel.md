---
title: "how to boot into newly install kernel"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by vanthai26 on 2006-10-20
Hi,

I have just down load source code for kernel linux-2.6.17.14 onto my ubuntu linux and was able to build and install it on my ubuntu linux machine. However I am not sure what I need to set to allow me to reboot into my newly install kernel instead of the old one. There is a mention of fixing menu.lst file but I am not quite sure on how to do it. Can some one please help...

Thanks so much

Bar..

---

### Post by bsussman on 2006-10-20
Are you upgrading due to a bug fix?  A new feature?  For Adventure?

the /boot/grub/menu.lst is very well documented in comments in itself - the simplest way is to duplicate one of the stanzas and change the relevant file names and the name for the stanza.  Make sure to put it below the auto-generate comment so that it does not get wiped out in the future.

Do not remove the current booting stanza until you have tested the new one - otherwise you might be left with an unbootable system and need to do recovery work, which, while not difficult, is extra labor.

---

### Post by vanthai26 on 2006-10-20
I am not quite sure what to do here can you be more specific..

Thanks

---

