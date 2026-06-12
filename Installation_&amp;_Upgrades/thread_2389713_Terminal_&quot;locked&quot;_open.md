---
title: "Terminal &quot;locked&quot; open"
date: 2018-04-20
forum: Installation &amp; Upgrades
---

### Post by Rixter69 on 2018-04-20
Was trying to install Ubuntu restricted extras and, to make a long story short, was told the terminal is 'open" elsewhere. Looked all around desktop, but I knew there wasn't another terminal open anywhere. So, my question being...what would cause the terminal to determine there is 'another" terminal open. After awhile, I tried to install a pkg. from software center and received same message-- "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? I rebooted, but same problem? What's going on?

TNX:

:confused:Rick

---

### Post by Frogs Hair on 2018-04-20
Try the following one at a time via copy and paste.

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
``` ```
sudo apt update
```

---

### Post by Rixter69 on 2018-04-20
RE: [I][B]Frogs Hair

   You Da Man...er FROG!!!  Thanx Your reply seems to have done the trick. Ahm... I'm new to this forum...where do I mark this thread solved?

THANX AGAIN:

Rick[/B][/I]

---

### Post by Rixter69 on 2018-04-20
Found   "mark this solved"

---

