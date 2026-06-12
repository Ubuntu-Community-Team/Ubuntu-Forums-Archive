---
title: "Want to boot to Command line"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by otetiani on 2012-10-15
So this might be backwards, but sometimes I have been known to be.

I want to boot 12.04 to command line vs X, and initiate X after when I need to, but can't find how I would disable X on boot up.

The reason is I'm getting lazy on using the command line unless I am not sure how to do it graphically.

---

### Post by Cheesemill on 2012-10-15
```
echo  "manual" | sudo tee -a /etc/init/lightdm.override
```
You can then use startx whenever you want a GUI.

---

### Post by otetiani on 2012-10-15
Thanks, missed looking for disabling lightdm, or the obvious tag "boot without X"


this worked for me: [http://ubuntuforums.org/showthread.php?p=10798400#post10798400]("http://ubuntuforums.org/showthread.php?p=10798400#post10798400")"]

---

