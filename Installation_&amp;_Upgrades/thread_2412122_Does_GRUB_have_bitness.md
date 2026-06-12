---
title: "Does GRUB have bitness?"
date: 2019-02-08
forum: Installation &amp; Upgrades
---

### Post by benjamin38 on 2019-02-08
Hello,

Thank you for answers, or any light.

Question:
Does 32/64bit apply to the bootloader?

Context:
I have a USB thumb drive, onto which I have installed Xubuntu, both 32 and 64 bit version, in separate partitions.. I have all my stuff installed in these installations. Very useful. I use this as a great portable multi-tool, as well as just having my OS and environment with me. I'm highly mobile, and it comes in handy often.

I need the 32bit because I do sometimes encounter older 32bit machines and need to be able to boot up on those too.
I need the 64bit because 32bit is no longer supported by ever increasing packages and programs.
So it's the opposite. The default choice is 64bit, but I also need 32bit as sometimes that's the only option.

The question is: when installing the two instances, does the order of installation matter?
If the bootloader has 'bitness', I'd need to install the 32bit version last, so as to have the 32bit bootloader overwrite the 64bit, thus booting off all machines.
If the bootloader does not have 'bitness', I'd prefer to install the 64bit version last, so as to have it (the 64bit) be the first and default boot option.

I'm well aware that I can edit grub.cfg and make the default whatever I want. There are reasons why I don't want to do that.

Hope all is clear. Appreciate any answers
Thanks

---

