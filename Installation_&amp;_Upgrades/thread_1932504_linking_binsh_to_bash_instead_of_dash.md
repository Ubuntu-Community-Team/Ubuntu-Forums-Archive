---
title: "linking /bin/sh to bash instead of dash"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-02-27
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

i prefer bash over dash.  bash is a traditional linux program and is on (almost) all linux systems.

alt + f2

gnome-terminal

run

to see if your running dash run

ls -al /bin/sh

```

sudo rm /bin/sh

```

```

sudo ln -s /bin/bash /bin/sh

```

ls -al /bin/sh

should now point to bash

to run dash again

```

sudo rm /bin/sh

```

```

sudo ln -s /bin/dash /bin/sh

```

---

### Post by MG&amp;TL on 2012-02-27
This should probably be in tutorials and tips, not in the help sections...just for future reference. Although nice work. :)

---

