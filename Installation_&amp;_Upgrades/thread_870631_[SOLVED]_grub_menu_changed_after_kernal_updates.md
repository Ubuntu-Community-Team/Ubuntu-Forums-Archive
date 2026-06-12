---
title: "[SOLVED] grub menu changed after kernal updates"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by Sisophon2001 on 2008-07-26
My wife's computer is set up to duel boot WinXP (her primary OS) and Ubuntu (which she uses for some games). She knows how to keep Ubuntu up to date, but the problem is that if there is a kernel update, the grub menu order is changed, and her computer stops booting into WinXP as default, until I fix things up.

Is there a way to fix the order of the grub menu so that WinXP will always be the default, even after a kernel update?

Thanks

Garvan

---

### Post by iaculallad on 2008-07-26
> **Sisophon2001 said:**
> My wife's computer is set up to duel boot WinXP (her primary OS) and Ubuntu (which she uses for some games). She knows how to keep Ubuntu up to date, but the problem is that if there is a kernel update, the grub menu order is changed, and her computer stops booting into WinXP as default, until I fix things up.

Is there a way to fix the order of the grub menu so that WinXP will always be the default, even after a kernel update?

Thanks

Garvan

I can't think of a fix that will auto-fix the order of the GRUB menu whenever new kernel updates are installed. The only thing you could do is edit your /boot/grub/menu.lst file and change the settings of **default** (start from counting 0 rule) to match that of winxp's setting:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
...
**default     0**
...
```

---

### Post by Herman on 2008-07-26
:) You could cut the entire Windows booting stanza from the bottom of your /boot/grub/menu.lst file and paste it further up, around the middle of the file, *above* the line that marks the [DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST").

Don't put foreign boot stanzas inside the [DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST") or they will be automagically deleted at every kernel update.

The beginning and end of the [DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST") is clearly marked. :)

---

### Post by Sisophon2001 on 2008-07-26
Thanks to both, I think Herman's idea is what I am after. I will give it a try.

Garvan

---

### Post by Liakath on 2008-07-26
Dear Sisophon2001,

Alternately you may install **Startup Manager** through Synaptic and you can access it from **System > Administration > Startup Manager** and use it to set up the default OS to boot in the first tab **"Boot options"**. See the first screen shot

Then set grub to update the default OS to boot across kernel updates through its **"Advanced"** tab. I have attached the 2nd screen shot showing this option; it is the third option in Misc. listing under "Advanced" tab.

Hope this will be an easier option for your problem.

Liakath

---

### Post by Sisophon2001 on 2008-07-26
Even better. I installed startup manager, and set the options through that.

Thanks

Garvan

---

### Post by Liakath on 2008-07-26
Dear Garvan,

> **Sisophon2001 said:**
> Even better. I installed startup manager, and set the options through that.

Thanks

Garvan

You are welcome and very happy to be of help.

Liakath

---

