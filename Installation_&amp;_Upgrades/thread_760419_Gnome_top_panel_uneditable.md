---
title: "Gnome top panel uneditable"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Nem1976 on 2008-04-20
I hope this is in the right forum section.  I did the upgrade from Gutsy to Hardy this morning and everything is working perfectly except my top panel I can't edit it.  If I right click an empty spot on the panel all I get is help and about this panel.  

I logged into my other profile and it works fine but it's a plain profile no bells and whistles.  Just the 1 profile has this issue.  Any suggestions?

---

### Post by unutbu on 2008-04-21
One of the dot-config files in your home directory must be incompatible with Hardy's gnome-panel.

My guess is it's something in either .gconf or .gnome2.

First save your config files:
```

tar cf gconf.tar ~/.gconf
tar cf gnome2.tar ~/.gnome2
```

Log out so gnome stuff is not running.
Press CTRL-ALT-F2 to get to a text console. Log in.

Remove your gnome config files. Next time you log in, gnome will realize there are no config files and will copy the default settings into your account (just like the other 'profile').

```

rm -rf ~/.gconf
rm -rf ~/.gnome2
```

Log out of the text console, log in via GDM.
Your gnome panel should work.
Hopefully, there is not too much reconfiguration you'll have to do to get your desktop the way you like it.

If you want to restore your old .gconf and .gnome2, run

tar xf gconf.tar
tar xf gnome2.tar

When you are satisfied gnome is working the way you want, don't forget to delete the tar files.

---

### Post by Nem1976 on 2008-04-22
Thanks for the help actually I found this command 

gconftool-2 --recursive-unset /apps/panel

In this post and it fixed my issue.


[http://ubuntuforums.org/showthread.php?p=4766200#post4766200](http://ubuntuforums.org/showthread.php?p=4766200#post4766200)

---

### Post by unutbu on 2008-04-22
Thanks for the heads-up.

---

