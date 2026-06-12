---
title: "Synaptic not locking package - why?"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by oceanmajk on 2008-07-26
I tried locking my current php5 install inside of synaptic because it's compiled with full gd support and other nuances, but even though synaptic shows that it is locked, it still is trying to downgrade it when I mark all upgrades.

I found an old forum post that shows how to lock it, which worked, but I'd like to understand why this is...

```
echo "php5 hold" | sudo dpkg --set-selections
```

Can anyone shed some light on this issue? I just want to understand why synaptic isn't doing this already. Thanks.

---

### Post by zvacet on 2008-07-26
```
sudo aptitude forbid-version packagename
```

---

