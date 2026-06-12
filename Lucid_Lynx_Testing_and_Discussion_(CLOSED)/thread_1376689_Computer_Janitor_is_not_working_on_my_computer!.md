---
title: "Computer Janitor is not working on my computer!"
date: 2010-01-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2010-01-09
Computer Janitor is not working on my computer.

Ubuntu 10.04 Long Term Support Alpha 1 as an Upgrade from Ubuntu 9.10 Release 2 Web.

---

### Post by plun on 2010-01-09
Nope, stone dead, file a bug please.....

```
plun@plun-laptop:~$ gksudo computer-janitor-gtk
Traceback (most recent call last):  File "/usr/sbin/computer-janitor-gtk", line 30, in <module>
    app.run(computerjanitorapp.GtkUserInterface)
  File "/usr/share/computerjanitor/computerjanitorapp/app.py", line 101, in run
    ui.run(options, args)
  File "/usr/share/computerjanitor/computerjanitorapp/ui_gtk.py", line 211, in run
    self.create_column('unused_treeview', self.unused_filter)
  File "/usr/share/computerjanitor/computerjanitorapp/ui_gtk.py", line 291, in create_column
    treeview = self.widgets[widget_name]
KeyError: 'unused_treeview'

```

---

### Post by VMC on 2010-01-09
> **plun said:**
> Nope, stone dead, file a bug please.....

```
plun@plun-laptop:~$ gksudo computer-janitor-gtk
Traceback (most recent call last):  File "/usr/sbin/computer-janitor-gtk", line 30, in <module>
    app.run(computerjanitorapp.GtkUserInterface)
  File "/usr/share/computerjanitor/computerjanitorapp/app.py", line 101, in run
    ui.run(options, args)
  File "/usr/share/computerjanitor/computerjanitorapp/ui_gtk.py", line 211, in run
    self.create_column('unused_treeview', self.unused_filter)
  File "/usr/share/computerjanitor/computerjanitorapp/ui_gtk.py", line 291, in create_column
    treeview = self.widgets[widget_name]
KeyError: 'unused_treeview'

```
I followed the trail on this one, and gave a "affects me too" to one of the already reported bug.

---

### Post by k3lt01 on 2010-01-09
There are a few bugs reported on this already. One of them, mine, is number 503656. Try to match yours with the correct one if it is the same.

---

### Post by VMC on 2010-01-09
> **k3lt01 said:**
> There are a few bugs reported on this already. One of them, mine, is number 503656. Try to match yours with the correct one if it is the same.

That would be the one. Me and 37 others.

---

### Post by k3lt01 on 2010-01-09
> **VMC said:**
> That would be the one. Me and 37 others.It all helps the devs to make the system even better.

---

