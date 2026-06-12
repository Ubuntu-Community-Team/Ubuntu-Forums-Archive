---
title: "Python 2.7 to Python 3"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by anirudhbhardwaj19 on 2011-06-14
I have do just Installed Python 3.2 on my system but have to make it coexist with python 2.7 which is currently default with ubuntu 11

How can I remove 2.7 so and make python 3 the default .

Or when is the Debian default version change due !!

---

### Post by cipherboy_loc on 2011-06-14
You can **remove** python2.7 with:

```

sudo apt-get remove python2.7 ; sudo apt-get autoremove

```

But if you just want to set a program to run with python3, then either launch it with: 
```

python3 /path/to/file

```

or edit the first line (won't work on all scripts) to this: 

```

#!/usr/bin/env python3

```

If something similar doesn't exist already in the script, add that line to the top (and don't replace anything).

---

