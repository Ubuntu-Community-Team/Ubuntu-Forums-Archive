---
title: "Acpi"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by Frihet on 2005-01-30
I've just installed ubuntu on my IBM600X laptop.  Things seem to be going well at this point.

ACPI does not appear to be active.  How can I turn it on?

Thanks!

---

### Post by az on 2005-01-30
Try adding acpi=force to your kernel line in 
/boot/grub/menu.list

for starters.

---

### Post by Frihet on 2005-01-30
Thanks, azz!

I think the file is actually menu.lst.

There is a lot of stuff in there.  Does it make any difference where I place the command?

---

### Post by az on 2005-01-30
Use the stanza that is the default for your Ubuntu system.

---

### Post by Frihet on 2005-01-31
Thanks again, azz.

However, I do not understand what this means: "Use the stanza that is the default for your Ubuntu system."

I appreciate the time you are spending with me.  I can easily edit menu.lst, but I just don't know what I'm supposed to be doing in there.  Because I have altered nothing, I suspect the defaults are present now.

---

### Post by Frihet on 2005-01-31
Ok, azz.  I figured it out.  Acpi=on in the menu.lst file does nothing.  Acpi=force causes a kernel panic (I guess).  After logon, I have no desktop and the usb mouse is dead.  The laptop pointer still works, but there is nothing to point to.  I'm guessing this kernel simply does not have stable acpi support.

ACPI works fine on this box with Mandrake.

I was able to bail out and edit from vi to get rid of the acpi load string.  Everything is fine.

I'm not going to take this any further.  I'll wait for HH.

Thanks!!!

---

