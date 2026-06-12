---
title: "Run Skype with video on intrepid 64-bit with wrapper script"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by b.q.wemer on 2008-10-14
Hi to all 64-bit beta testers,

some may have already experienced, that using the recommended LD_PRELOAD hack ends up in the following error:

> ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

This is cause the wrong lib is used. Install lib32v4l-0 packet instead and use

> LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

I have automated this by doing the following steps:

1. Rename skype to skype.bin```
sudo mv /usr/bin/skype /usr/bin/skype.bin
```

2. Make an executable script with the following content an put it to /usr/bin
```
#!/bin/bash

SKYPE_BIN_PATH="/usr/bin"
LIBV4L="/usr/lib32/libv4l/v4l1compat.so"

LD_PRELOAD=${LIBV4L} skype.bin

exit 0
```(BTW: Improvements always welcome.)

3. Start skype as usual.

HTH

---

### Post by loell on 2008-10-14
in addition, you'll gonna haveto install libv4l

from [https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

before preloading it.

---

### Post by b.q.wemer on 2008-10-14
Thanks for your addtion!

Alternatively you can install libv4l-0 from intrepid repos. ;-)

Bye

---

### Post by loell on 2008-10-14
> **b.q.wemer said:**
> 
Alternatively you can install libv4l-0 from intrepid repos. ;-)


ahh! so libv4l 0.5 made it to intrepid after all. :)

---

