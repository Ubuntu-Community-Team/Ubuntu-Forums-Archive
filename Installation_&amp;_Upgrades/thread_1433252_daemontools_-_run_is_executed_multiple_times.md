---
title: "daemontools - run is executed multiple times"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by sokrates_sf on 2010-03-18
I installed daemontools based on [http://mihasya.com/blog/daemontools-0-76-on-ubuntu-9-04/](http://mihasya.com/blog/daemontools-0-76-on-ubuntu-9-04/) 

- Patched it as suggested

- Created /service/.../run and tested with the "echo" as described in install instructions. 

- What I am getting is a continuous output ("echo")

- Any application 'exec' calls in 'run' result in creation of multiple application instances. 

Anyone any ideas ?

---

### Post by sokrates_sf on 2010-03-19
... adding a 'sleep' fixed the issue: 

#!/bin/bash
exec [YOUR_APPLICATION]
sleep 15

---

