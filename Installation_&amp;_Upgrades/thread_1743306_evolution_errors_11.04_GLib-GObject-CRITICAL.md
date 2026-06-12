---
title: "evolution errors 11.04 GLib-GObject-CRITICAL"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by allen@tiniusfamily.net on 2011-04-29
Just upgraded to ubuntu natty and evolution hangs.    Receive the following errors....

[email]allen@FA2096349:~/.evolut[/email]ion$ evolution

(evolution:25316): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:25316): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'


The evolution app starts, but all you get is Loading... for the folders in the side bay and the app is hung.   Nothing is selectable and you have to CTRL-C out of it or use the kill app.:(

---

### Post by mörgæs on 2011-04-29
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by allen@tiniusfamily.net on 2011-05-02
Thanks for the post and everything is supported, worked in a previous version and so far, evolution is the only error I am having so far.  My install is pretty vanilla.   I assume evolution is working for many who are on 11.04.   Any other ideas?

---

### Post by allen@tiniusfamily.net on 2011-05-03
mv ~/.local/share/evolution ~/.local/share/evolution.old
start evolution
Still receiving the error from above, but it rebuild the databases and everything seems to be working.

---

