---
title: "htop won't run"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gletob on 2009-03-02
I'm having a problem where running htop in gnome terminal just show a blank screen and running in a VT it does nothing and won't respond to control+c or killing the process.

---

### Post by dentaku65 on 2009-03-03
Running fine here. Try to reinstall it
```
sudo apt-get --reinstall install htop
```

or rename this:
```
mv ~/.htoprc ~/.htoprc.original
```
and restart htop

---

