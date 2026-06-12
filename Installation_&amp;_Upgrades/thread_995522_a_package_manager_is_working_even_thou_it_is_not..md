---
title: "a package manager is working even thou it is not."
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by ultimatsz on 2008-11-27
the notification "a package manager is working" appeared even thou any package manager is not working..

could there be any background package manager working? like some virus?

what can i do?

thanks

---

### Post by taurus on 2008-11-27
See if there is something running in the background.

Applications -> Accessories -> Terminal
```
ps -A
```
I highly doubt if there is a virus!

---

### Post by robert shearer on 2008-11-27
open a terminal and type

```
top
```

If you see something in the output like "synaptic" or Update manager" then a package manager is working.

Most likely the daily update to of package information was happening.(unless you have configured it to not happen?)

This can take a little while if you are on dialup.?

Next time it happens check with top as above.

If that is not the problem/answer to your question please post more info.

EDIT.  I am such a slow typist... beaten to it by taurus.

---

