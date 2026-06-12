---
title: "Reinstalling issues"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Solitary_ on 2007-10-23
Hey guys sorry if this has been done before, I tried my best to find what I was looking for before posting but couldn't.

Ok this is my problem (assuming I can get it accross without sounding like a complete idiot)

Say i install something for example "apt-get install abc" and then accidentally delete a file, i use "apt-get remove abc" to complete remove the lot so i can start fresh, but when i re-install I am still missing the file i deleted by accident.

Is there a way to force a complete re-install with the missing file included?

Thanks for any help you can give :)

---

### Post by LLRNR on 2007-10-23
Try "aptitude purge abc" and then attempt the reinstall.

---

### Post by Solitary_ on 2007-10-23
Thanks, i will have a go :)

---

