---
title: "workspace switcher not working properly?"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jwssr on 2009-09-04
starting with alpha 5   workspace switcher which allows for multiple rows and multiple columns now only allows 0 as as option.

The default is set at 2....if you need more than 2 workspaces...no luck...

anyone else seeing this?

---

### Post by cyberkilla on 2009-09-05
Yup, I'm seeing it too.

---

### Post by kansasnoob on 2009-09-05
Same thing here!

---

### Post by Skipnaz on 2009-09-06
Same thing here. Since I don't get a popup to report it...just have to wait it out, someone will take care of it before release or maybe this is the way its going to be

---

### Post by zika on 2009-09-06
Since I've had 4 workspaces already, it gives me 4 even though in Preferences it has zeros in both places ... So, it is marked somewhere in some file that I have 4 workspaces. That might help ... Just to find in which file is that written ...
(gconf-editor->apps->metacity->general->num_workspaces =4)

---

### Post by neferty on 2009-09-06
This bug's already reported. [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/423493](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/423493)
You can still adjust the number of workspaces through compiz configuration manager as a temporary solution.

---

