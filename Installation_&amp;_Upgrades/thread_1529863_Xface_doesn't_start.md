---
title: "Xface doesn't start"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by zionwing on 2010-07-12
I installed XFCE to test it on my ubuntu(gnome) 10.04
I restart the computer and tried with xfce session , but it immediately  returns to the logon screen :/, and i tried to login with root account and it works but just with the root acount
i don't know what is the problem...with gnome I have  no problem.

I hope you can help me

sorry for my english :)

---

### Post by thahir1986 on 2010-07-13
Just Login as root and go to the home <user> directory and u can find the hidden file .xsession & open the file and append

```
#Start XFCE
exec startxfce4
```save and exit.  Give the link for .xinitrc

```
ln -s .xsession .xinitrc
```
I hope this would be useful for u:D

---

