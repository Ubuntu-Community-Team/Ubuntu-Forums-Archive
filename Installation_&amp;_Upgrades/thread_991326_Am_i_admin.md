---
title: "Am i admin?"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by vandyer on 2008-11-23
Hi - I've tried using the search facility but still don't seem to get the right answers. 

I installed Ubuntu 8.10 a few days ago. During installation i created a user called "tony". I now need to alter a file (following instructions in another post regarding a different issue) and i do not have sufficient privileges. 

So, i take it that my account "tony" is not the same as "admin". As i'm sure i  didnt set up the "admin" account, what is the password?

Van

---

### Post by perlluver on 2008-11-23
To become "root" or admin, you will use sudo gedit /your/file.  sudo gives you temporary admin rights.  You will not always be root, because this is unsafe, and you could potentially delete important files.

And might I recommend looking this over, it explains it in more detail: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

