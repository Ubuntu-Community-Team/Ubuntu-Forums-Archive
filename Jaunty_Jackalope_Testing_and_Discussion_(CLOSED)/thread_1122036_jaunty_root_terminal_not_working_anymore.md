---
title: "jaunty: root terminal not working anymore"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ddastoor on 2009-04-10
Hi I upgraded from ubuntu 8.10 to jaunty yesterday and suddenly my root terminal does not work. I provide my password, then it comes on and vanishes.

Any ideas ?
Thanks - Dinshaw

---

### Post by adamitj on 2009-04-10
How are you entering your root terminal?

---

### Post by JackH79 on 2009-04-11
Same problem here. It's the preinstalled app launcher under System Tools with the following command: ```
gksu /usr/bin/x-terminal-emulator
```.
Sudo su works though.

---

### Post by ddastoor on 2009-04-12
yes, that's correct.

---

### Post by chrisccoulson on 2009-04-12
That is because when you run gnome-terminal with gksu (which is what x-terminal-emulator is pointing too), it can't access the gconf daemon and just exits. It's already reported on Launchpad and on the upstream Bugzilla.

---

### Post by maciu on 2009-04-12
yup that problem is pretty annoying you can track it here [https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575)

---

