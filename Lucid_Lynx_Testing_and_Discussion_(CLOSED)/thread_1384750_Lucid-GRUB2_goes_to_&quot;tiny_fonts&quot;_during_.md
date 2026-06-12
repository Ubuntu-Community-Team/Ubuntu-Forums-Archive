---
title: "Lucid-GRUB2 goes to &quot;tiny fonts&quot; during boot.  This is annoying."
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-01-18
How to revert it to all one text size, preferably the same size as when booting begins?

---

### Post by vade on 2010-01-18
You can disable kernel mode setting, i.e. append nomodeset to kernel command line.

---

### Post by vishalrao on 2010-01-18
did you add/change any grub2 settings like gfxmode or add "vga=xxxxx" to the kernel/linux boot options? if so , remove/revert them and try again?

---

### Post by emarkay on 2010-01-18
> **vishalrao said:**
> did you add/change any grub2 settings like gfxmode or add "vga=xxxxx" to the kernel/linux boot options? if so , remove/revert them and try again?

This is what I have in : /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

Also this line :
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
relates to this thread: [http://ubuntuforums.org/showthread.php?t=1384753](http://ubuntuforums.org/showthread.php?t=1384753)

Other than that, this is a pretty much "un-texturally molested" (nearly nothing edited in console)  clean install.

---

### Post by dino99 on 2010-01-19
> **emarkay said:**
> How to revert it to all one text size, preferably the same size as when booting begins?

Startup-Manager is your friend  :D

---

### Post by ranch hand on 2010-01-19
If you are talking about the messages during the boot process this has nothing to do with grub at all.  It is done before that stuff comes up.

This is not a bug it is a feature.  It is a "more efficient way to display information".  I think it is a little hard to read myself.

---

### Post by emarkay on 2010-01-19
> **dino99 said:**
> Startup-Manager is your friend  :D


Um, ok, now tell me where/what there affects this?  :)

---

### Post by phillw on 2010-01-20
> **ranch hand said:**
> If you are talking about the messages during the boot process this has nothing to do with grub at all.  It is done before that stuff comes up.

This is not a bug it is a feature.  It is a "more efficient way to display information".  I think it is a little hard to read myself.

Heck, it boots doesn't it ? One should be grateful for such things 

:lolflag:

All the hours put into making the boot look pretty ... Gee... Once the LTS is released, I'm looking forward to booting at least once a year :D The scary bit for me to learn is how to switch linux kernels 'on the fly' - I can forsee a few crashes with that ;-)

Regards,

Phill.

---

