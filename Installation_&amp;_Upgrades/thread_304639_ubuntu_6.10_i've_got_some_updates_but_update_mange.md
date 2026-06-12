---
title: "ubuntu 6.10: i've got some updates but update manger won't install them!"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Lotti on 2006-11-22
hello.. i have a weird problem..

i installed a fresh ubuntu 6.10 and all work very well. expect for 1 thing. the updates manager.

every day (when updates are out) the updates notifier says to me that i got n updates to do.

when i click on "install updates" it says to me: "verifying updates"..

when it reaches 100% it doens't upgrade anything.

so i have to do it by console. (and now i don't remember the commands.. i'm new).

how to fix this?

---

### Post by rbalfour on 2006-11-22
From console

$ sudo apt-get update
$ sudo apt-get upgrade

---

### Post by GertDalPozzo on 2006-11-24
I've the same problem.
I can update packages using synaptic, so it isn't really a great problem, but it's annoying being unable to directly use update manager.

---

