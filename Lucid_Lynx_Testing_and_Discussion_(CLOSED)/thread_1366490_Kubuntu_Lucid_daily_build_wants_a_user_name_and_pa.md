---
title: "Kubuntu Lucid daily build wants a user name and password?"
date: 2009-12-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by exploder on 2009-12-28
Just like the title says... How are you supposed to check this out?

---

### Post by rustybronco on 2009-12-28
problem with this bug possibly?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)
> Just ctrl+alt+f1, then create a new user account & password w/root privileges:

sudo useradd -d /home/username -m username
sudo passwd username
sudo adduser username admin

Then ctrl+alt+f8.

Many thanks to ASriazh @ Ubuntu forums.

---

### Post by exploder on 2009-12-28
Thank you!

---

