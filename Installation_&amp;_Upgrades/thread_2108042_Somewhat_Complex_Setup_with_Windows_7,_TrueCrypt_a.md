---
title: "Somewhat Complex Setup with Windows 7, TrueCrypt and Ubuntu"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by Paranoid Geekazoid on 2013-01-23
I'll start with some preamble: my current (older) laptop is setup like...

GRUB v1 in MBR
(hd0,0) Windows XP *(encrypted with TrueCrypt)*
(hd0,1) Ubuntu 9.04 *(non-encrypted honeypot)*
(hd0,2) swap
(hd0,x) [I][other partitions]

[/I]Using some modifications on [this guide]("http://ubuntuforums.org/showthread.php?t=761530"), I setup GRUB to chainload the TrueCrypt bootloader only upon by explicit selection to open the boot menu (Ubuntu was the default OS).  The idea being that a not-so-sophisticated attacker would automatically boot into the Ubuntu honeypot.

Oddly, when I upgraded TC from 6.0a to 7.1a, instead of overwriting GRUB (which is what I expected it to do), it reversed the setup: TC was now the default bootloader and kicked it over to GRUB upon pressing ESC.  This setup is sort-of OK as TC 7.1.a enables you to create a custom boot prompt, but I still prefer it the other way.

**Onto the meat of the thread: **I have a new laptop with Windows 7 and I would like to set it up in the same way as described at the beginning of this thread.

However, I'm unfamiliar with GRUB2 and UEFI.  My virtual machine experiments have been unsuccessful thus far.

How do I go about setting this up?  Maybe there's a better way to achieve this  with a different configuration?  I'm open to ideas.

---

### Post by oldfred on 2013-01-23
It does not look like it will work yet. UEFI is too new for truecrypt.

[http://www.truecrypt.org/future](http://www.truecrypt.org/future)

---

### Post by Paranoid Geekazoid on 2013-01-23
Oh ... well, dang.

So, will it work if I disable UEFI and use legacy boot?  Can I still install it and open file containers?

Like I said, I'm open to suggestions :|

---

