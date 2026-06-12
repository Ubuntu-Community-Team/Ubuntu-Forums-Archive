---
title: "How hide an user from GDM users list?"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nuovodna on 2009-10-15
Hi, how can i hide an user (that i use only from ssh tunnel) from GDM users list?
I tried to setting "hide user list" from gconf-editor but nothing happens (I have restarted gdm, of course)

Thanks

---

### Post by electronpositivo on 2009-10-28
Try with this in terminal:

```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type Boolean --set /apps/gdm/simple-greeter/disable_user_list True
```

This command hide ALL users from the list in gdm.

Do you know how specify users who should be listed individually?

---

### Post by flxndn on 2009-10-28
I want a user no to be shown in the gdm users list. How can I do it?

Thanks

---

