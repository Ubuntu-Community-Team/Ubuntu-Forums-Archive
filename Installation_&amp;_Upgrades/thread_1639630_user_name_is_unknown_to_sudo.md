---
title: "user name is unknown to sudo ??"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2010-12-06
```
root@ubuntu:/home/ramaswamy# synaptic
No protocol specified

(synaptic:1564): Gtk-WARNING **: cannot open display: :0
root@ubuntu:/home/ramaswamy#   
```              
if i use menu to invoke synaptic or adept it says 

your username is unknown to sudo 
message comes up

how to correct this?
i am on kde-3.5.12

---

### Post by sgosnell on 2010-12-06
Why are you running as root?  Are running from a liveCD?  If so, you can't install anything.

---

### Post by ramaswamyps on 2010-12-07
it is already installed ubuntu-10.10 desktop
i cannot use aynaptic from my user login.
it says i am not sudo er
thats why trying as su
anyways i cannot invoke synaptic

---

### Post by sgosnell on 2010-12-07
Add yourself to sudoers.  [Let me google that for you](http://lmgtfy.com/?q=add+user+to+sudoers+ubuntu)

---

