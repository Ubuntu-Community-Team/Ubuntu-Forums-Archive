---
title: "&quot;gksu nautilus&quot; not working after 8.04 upgrade - GLib-GObject-ERROR"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by uberpenguin on 2008-05-07
Ive just recently upgraded my box from 7.10 to 8.04. 
Everything seems fine except I now cannot run nautilus as root via gksu?
I can run it no problem without gksu but when I try to run it as root I now get this error msg :-


 /home/user/$:  gksu nautilus

Initializing nautilus-share extension

GLib-GObject-ERROR **: g_type_plugin_*() invalidly modified type `GLocalFileInputStream'
aborting...

This worked fine before the upgrade. Can anyone suggest what I need to do to fix this?
Appreciate any feedback you can give me.

---

### Post by Daedal Dementia on 2008-06-16
doubt this will help, but i had a similar problem

i had 8.04 and got a kernel upgrade and lost nautilus.

you've probably tried this but 

```
sudo nautilus
``` ?

sorry if i dont help...

---

