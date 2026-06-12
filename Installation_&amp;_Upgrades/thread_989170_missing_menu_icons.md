---
title: "missing menu icons"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by cyclocross on 2008-11-21
after an upgrade from hardy to intrepid, mayn of my root menu items for applications have turned into folder icons.  when I go to the menu editor and select them and select properties, nothing happens.  Does anyone have an idea on how to fix this?

---

### Post by alexey.brodovshuk on 2008-11-24
I had exactly the same problem.
And found the following solution:
Just remove the directory /home/username/.config/menus

```
sudo rm -r /home/username/.config/menus
```

or

```
sudo mv /home/username/.config/menus /home/username/.config/_menus
```
if you don't want to remove it

worked for me!

---

### Post by cyclocross on 2008-12-01
Thanks for the response alexey.brodovshuk, but your fix didn't fix the problem.  Anyone else have a fix for this?

---

