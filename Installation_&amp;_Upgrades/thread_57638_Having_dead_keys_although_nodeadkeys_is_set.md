---
title: "Having dead keys although nodeadkeys is set"
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by matthias_k on 2005-08-17
Hi,

in my xorg.conf, the nodeadkeys option is set for the keyboard driver:
> 
matthias:~$ less /etc/X11/xorg.conf | grep nodeadkeys
        Option          "XkbOptions"    "nodeadkeys"

However, in bash I still have to type ~+SPACE to get the tilde symbol. Same for the other usual dead keys.

How come?

---

### Post by matthias_k on 2005-08-18
Anyone?

---

### Post by matthias_k on 2005-10-11
I have solved this issue, somewhat.

The problem was GNOME overriding the X.org settings for keyboard mapping. You have to open the keyboard settings and select a keyboard map with the "nodeadkeys" option.

However, it didn't fully solve all my problems. For example, in aterm I still can't use the "pos1" and "end" keys, they only print a tilde when hitting them.

Still, any help appreciated, it's getting annoying :-/

---

