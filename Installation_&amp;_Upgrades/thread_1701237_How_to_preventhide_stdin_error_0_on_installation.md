---
title: "How to prevent|hide: stdin error 0 on installation"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by n~kf)}BW% on 2011-03-06
Hello,

I'm working on a custom Ubuntu Live CD and i have some problem with "stdin error 0" appearing before the splash screen... How can i prevent this? Or hide|redirect the output from stdin?

Best regards

---

### Post by An Sanct on 2011-03-06
Hello there!

Could you redirect it to null?

```
> /dev/null
```There are also a lot of forums, that mention problems while loading the casper file system (since its a CD, it cannot have one) so for first, try to build a live USB. After you have that, move (with boot sector and all) it to an ISO and try it on a virtual machine.

[Launchpad issue]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/406192") (note: for Karmic tho)

Pa lep pozdrav ;)

---

### Post by n~kf)}BW% on 2011-03-07
It's not that easy to redirect boot output to null ;) How can i do that? I don't think this can be done so early in the boot process...

Of course i'm testing it in virtual appliance :D It is working but this error at the beginning is annoying... It's not even a true error...

Pozdrav :D

---

