---
title: "SH Problems"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by Ryoushi19 on 2007-07-30
Whenever I try to run a shell script from the command line on 7.04, it returns that there is a syntax error, usually involving parenthesis.  The oddity here is that the same shell scripts I speak of worked on other distros, as well as 6.06... any help on this one?

---

### Post by Ryoushi19 on 2007-07-30
...Any help on this one?

---

### Post by bernied on 2007-07-30
Could it be because you are using a different shell. Do you specify which shell to use on your first line?
```
#!/bin/sh
```or```
#!/bin/bash
```

---

### Post by Ryoushi19 on 2007-07-30
I tried specifying SH and it seems to be working fine now.  Thanks!  ^.^

---

