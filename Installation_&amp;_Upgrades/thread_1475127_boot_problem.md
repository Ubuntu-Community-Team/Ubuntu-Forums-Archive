---
title: "boot problem"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by poupik on 2010-05-06
hello

i am **really** new at this..
i installed ubuntu today, alongside windows.
my disk was partitioned before the installation.

i managed to boot a couple of times before it started giving me a "no file system" message and a 'grub>' prompt instead of the grub menu.

i booted from the installation cd.

of course i started messing around.. and now i have some more partitions, and some unallocated disc space that i cant put back together.

another thing i noticed is, that in the 'Disk Utility', there showed up a 'peripheral device' wich is 704 mb something with the title 'filesystem.squashfs' and declares that its 'device' is /dev/loop0.

i am really lost!
please help.

thank you

---

### Post by neonathon on 2010-05-06
first, don't touch that 704mb file. if it were on my computer, i would be avoiding that thing like the plague. second, have you altered any files with windows while Ubuntu was installed like a virus scan?

---

### Post by poupik on 2010-05-06
no. since i installed ubuntu i didnt run windows.

and ok, i will avoid it, but what should i do?

thanks

---

### Post by neonathon on 2010-05-06
1) don't upgrade grub.

2) what version of windows an ubuntu

---

### Post by poupik on 2010-05-06
(1) i wouldnt even if i knew how
(2) xp, 10.04

---

### Post by oldfred on 2010-05-06
From the liveCD run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

