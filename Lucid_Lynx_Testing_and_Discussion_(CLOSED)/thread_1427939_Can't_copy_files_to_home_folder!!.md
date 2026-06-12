---
title: "Can't copy files to home folder?!?!?"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by anaconda on 2010-03-12
Strange. I cant copy any file to my home folder. the result is exactly the same even if I use sudo. "Invalid argument"

Can copy files to other locations though. eg. /home/anaconda/Desktop works. 

```
anaconda@ubu10:~/Desktop$ sudo cp test.txt /home/anaconda
[sudo] password for anaconda: 
cp: cannot create regular file `/home/anaconda/test.txt': Invalid argument

```
Anyone having the same problem? Oh. and nautilus cant copy the file either.

---

### Post by labinnsw on 2010-03-13
Try these commands and then try again.
```
chmod 644 .dmrc
chmod 700 ~
```

---

### Post by anaconda on 2010-03-15
Thanks, but The problem solved itself.

I just installed updates and rebooted, and after that home-folder has worked normally.

---

