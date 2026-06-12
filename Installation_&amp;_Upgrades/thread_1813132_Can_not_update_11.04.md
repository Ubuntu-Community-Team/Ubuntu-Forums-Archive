---
title: "Can not update 11.04"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by dryfire on 2011-07-27
Running 11.04 on a stable computer. Full internet access for browsing, I am writing this message on her. When I attempt to update, or download any Ubuntu packages, I get: 
"Failed to download package files
Check your Internet connection."

Any help appreciated.



Jim

---

### Post by MG&amp;TL on 2011-07-27
Are you updating via terminal, or 'update manager'?

If via update manager, a terminal always seems to be more reliable than software, so try typing:

```
sudo apt-get update
```

Of course, if you already did that, then not a clue. Try choosing a different mirror.

---

### Post by dryfire on 2011-07-27
> **MG&TL said:**
> Are you updating via terminal, or 'update manager'?

If via update manager, a terminal always seems to be more reliable than software, so try typing:

```
sudo apt-get update
```

Of course, if you already did that, then not a clue. Try choosing a different mirror.


That did it. The updates were found, using the terminal.
Then, the update manager installed all of them perfectly. And, now the "install new software" works as well.

Thanks,
Jim
nothing lasts, nothing is finished, nothing is perfect and nature bats last.

---

### Post by MG&amp;TL on 2011-07-27
No problem, had this issue myself. :D

Mark thread as 'solved' please! :)

---

