---
title: "Newbie noob Question"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by morbidxbean on 2008-06-12
ok its been asked about 11234 times now but how do i navigate to a certian folder on my desktop??? w/ the terminal   lets use the folder name  "doom" for example  what do i type?

---

### Post by omi291 on 2008-06-12
Let's say "doom" is on the desktop. in the terminal, just type 

```
cd /home/<your username here>/Desktop/doom
```

check out this thread for some more terminal info:

[http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners](http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners)

---

### Post by tamoneya on 2008-06-12
if you had a folder on your desktop named doom you could go like this in terminal:```
cd ~/Desktop/doom
```
cd: change directory
~: This is your home directory.  it is the shortcut for saying /home/username
Desktop: this would be your desktop
doom: this is the folder on your desktop

Also the title "Newbie noob question" is very undescriptive.  It helps other forum members if you use something more descriptive like "navigating folders in terminal"

---

### Post by morbidxbean on 2008-06-12
Well i get this :(

```
jimbo@jimbo-desktop:~$ cd ~/desktop/doom
bash: cd: /home/jimbo/desktop/doom: No such file or directory

```

---

### Post by morbidxbean on 2008-06-12
Ahh ok its case senseitive
...thanks!

---

