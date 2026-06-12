---
title: "[SOLVED] Shutdown Problems"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by kierpaul on 2008-09-01
This is minor, but can anyone help me? When I shutdown Ubuntu it powers all the way down and then after about a second it powers back up? This is intermittent as well it does not always do it! Thank you if anyone has a solution to this!

---

### Post by manishtech on 2008-09-02
Try this,

When you want to shut down your system, click on Applications>Accessories>Terminal

then type

```
sudo init 0
```

and see what happens, is the behavior same?
If the above code doesnt work, try this one

```
sudo poweroff
```

---

### Post by kierpaul on 2008-09-02
manishtech,

Thank you very much for your input and I will do these when I get home. I am at work right now and run Windows at work. I will get back with you!

---

### Post by kierpaul on 2008-09-02
manishtech,

When typing "sudo init 0" the system shutdown fine! Thank you and also is this temporary? I will let you know how it goes!

---

### Post by manishtech on 2008-09-03
sudo init 0 is just a command to change the system runlevel to 0. 0 means halt. poweroff is as the name suggests.

---

### Post by kierpaul on 2008-09-03
It worked and worked well and I am going to close out this post!

---

### Post by manishtech on 2008-09-04
:) to **kierpaul** , every problem has a solution.

BTW Thanks for commenting on my blog.

---

