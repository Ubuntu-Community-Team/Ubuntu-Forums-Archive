---
title: "make a ramdisk to put swap partition at installation"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Spare Tire on 2006-11-10
Can i make a ramdisk on LiveCD before installation and put the swap file on it? How to?
If i make on when i'm on live, will be dissapear after installation?

EDIT: I guess it would be easier to just install with swap dissabled and then make these once the installation is over. So, how do i dissable the swapping partition installation part?

---

### Post by kidders on 2006-11-11
Hi there,

_Do not_ mount a swap partition into RAM! The purpose of swap space is to page data. Tricking Linux into putting it all back into RAM can make your system behave very oddly when you stress it!

At the very least, it would just be a terribly inefficient way to manage memory, but at worst...

[LIST=1]
[*]Linux needs to clear out some RAM, so prepares to swap out chunks of it to "disk".
[*]The RAMdisk realises it needs to expand, and requests more RAM, which in turn causes more paging operations.
[*]Your system ties itself up in knots trying to handle the seemingly paradoxical situation where, in an effort to free memory, it seems to wind up with less of it.
[/LIST]

Can I ask why you wanted to try doing this?

---

### Post by lazyart on 2006-11-11
Yeah, that is a funny situation.  Ubuntu uses the swap when it runs out of memory.  I have to try this just to see it implode.

---

### Post by Darktiminator on 2007-01-02
I for one would like to know how to do this so as to run a pc from flash memory without burning the memory card out.

---

### Post by kidders on 2007-01-03
Hi there,

How would swapping to RAM be of use to you?

---

### Post by az on 2007-01-03
> **Darktiminator said:**
> I for one would like to know how to do this so as to run a pc from flash memory without burning the memory card out.

You mean use the flash drive as swap space?  No problem there.  Just format the partition on it as swap and mount it.

What do you mean burning the memory card out?  Do you mean consuming all the memory or are you talking about physical dammage?  No physical dammage will be cause by running Ubuntu.

---

