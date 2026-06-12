---
title: "installation using windows  installer"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by parusatra on 2013-04-16
Hi  everyone,
a more  than absolute beginner  here.
I  did  install  ubuntu alongside  windows  xp  using windows installer; had  a  good  look around and loved it. Only  problem it sits now  alongside  xp on my hard drive but I  don't know  how  to  access  my files  and programmes, retrieve my favourites on mozilla etc., in a word  the lot.
I'll  be  glad for  any pointers/starters

Cheers

---

### Post by Cheesemill on 2013-04-16
If you used the Windows installer then all of the files on your Windows drive should be in the /host directory.

---

### Post by Mark Phelps on 2013-04-16
> **parusatra said:**
> Hi  everyone,
a more  than absolute beginner  here.
I  did  install  ubuntu alongside  windows  xp  using windows installer; had  a  good  look around and loved it. Only  problem it sits now  alongside  xp on my hard drive...
Actually, since you used Wubi to install, it does not sit alongside Windows but INSIDE it.  Wubi creates a file INSIDE a Windows partition that serves as a Linux filesystem when running Ubuntu.  So, all your Ubuntu stuff is resident in that one file, inside an existing NTFS partition.

>  but I  don't know  how  to  access  my files  and programmes, retrieve my favourites on mozilla etc., in a word  the lot.
I'll  be  glad for  any pointers/starters

Cheers
Accessing your Windows files and programmes? Or, accessing your Ubuntu files and programmes?

As pointed out, you can access your Windows files (but not programmes) from inside Ubuntu by looking under /host in the Linux filesystem ... but you can't access your Ubuntu files from inside Windows.

---

### Post by parusatra on 2013-04-21
Hi,
many thanks to both of you. All  clear, done and dusted (for the time being)

---

### Post by Mark Phelps on 2013-04-21
Glad to see you got it working.  Please use the Thread Tools to mark this thread as SOLVED.

---

### Post by parusatra on 2013-04-22
Hi mark phelps,
it's late at  night here, but can't  find the right tool  under thread tools;  the only  options I see are : show the printable  version, e-mail this thread and unsubscribe from this  threrad. how do  i  mark it solved?

---

