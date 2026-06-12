---
title: "nautilus crashes"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-08-14
I have just installed todays updates. After a reboot I can login but there is no
background picture in Gnome and I hace a lot of error messages in the syslog.

```
macbook kernel: [  128.600445] nautilus[4877]: segfault at 0 ip 05bd0824 sp bfd47cc0 error 4 in libc-2.10.1.so[5b5d000+155000] 
```

---

### Post by plun on 2009-08-14
Well, I rebooted and have no trouble, latest update of 17.45 today.

Too much "experiments".....?   ;)

---

### Post by wayne_cat on 2009-08-14
I have created a new user ... the same problem. I had to set this option:

```
X-GNOME-AutoRestart=false
```in

```
/share/applications/nautilus.desktop
```now I have a background picture in Gnome but Nautilus still dies

```
rschmitt@macbook:~$ nautilus
Segmentation fault (core dumped)
```

Segmentation fault ... not good.

---

### Post by taavikko on 2009-08-14
Did you play with gconf?
Setting "show desktop"

---

### Post by wayne_cat on 2009-08-14
> **taavikko said:**
> Did you play with gconf?
Setting "show desktop"

show_desktop is enabled

I think you are talking about this thread:

[http://ubuntuforums.org/showthread.php?t=1228328&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=1228328&highlight=nautilus)

---

### Post by phenest on 2009-08-14
> **taavikko said:**
> Did you play with gconf?
Setting "show desktop"

You got in there before me. This is the only issue I have with Nautilus. Are you sure you haven't been tweaking it wayne_cat?

---

### Post by wayne_cat on 2009-08-14
> **phenest said:**
> You got in there before me. This is the only issue I have with Nautilus. Are you sure you haven't been tweaking it wayne_cat?

Haven't changed anything else ... a view days ago I had changed:

```
/apps/metacity/general/compositing_manager
```

from false to true ... but I disabled it again ( two days ago).

---

### Post by wayne_cat on 2009-08-14
Another strange effect ... I log in as my uers ... open a terminal ... change to user root.

If I start Nautilus from my root session the background picture changes from my picture to the picture of root's desktop.

edit: Fixed

I reinstalled gnome-session ... system works as it should.

---

### Post by Mafteah on 2009-08-14
I am having the same problem.
How to fix it?

---

### Post by taavikko on 2009-08-14
> **Mafteah said:**
> I am having the same problem.
How to fix it?

wayne_cat told this already:
> **wayne_cat said:**
> 
edit: Fixed

I reinstalled gnome-session ... system works as it should.

---

### Post by wayne_cat on 2009-08-14
> **Mafteah said:**
> I am having the same problem.
How to fix it?

You have to reinstall gnome-session

```
sudo apt-get install --reinstall gnome-session
```

---

### Post by Mafteah on 2009-08-14
Didn't help me.

apt-get --reinstall install gnome-session

---

### Post by wayne_cat on 2009-08-14
> **Mafteah said:**
> Didn't help me.

apt-get --reinstall install gnome-session

Your command is wrong .. it should be "apt-get install --reinstall gnome-session"

edit: I was wrong ... this also works

---

### Post by Toe on 2009-08-14
For some reason uninstalling brasero and installing nautilus-cdburner instead fixes these crashes on my machine. Switching back to brasero reintroduces the bug.

Can anyone confirm this?

---

### Post by nyarnon on 2009-08-14
> **Toe said:**
> For some reason uninstalling brasero and installing nautilus-cdburner instead fixes these crashes on my machine. Switching back to brasero reintroduces the bug.

Can anyone confirm this?

If you file a bug I will be glad to confirm. I wonder if Nautilus will ever become stable I still have to edit /etc/share/applications/nautilus.desktop every time it updates to set autorestart to false because of a respawning error that exists at least since intrepid. Seems to me the solution is staring the devs in the eye but somehow nobody seems to grasp the idea to distribute that file with the false setting as standard.
:lolflag:

---

### Post by Toe on 2009-08-14
Just discovered that a bug has already been filed.
Even better: a fix is already released :)

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/413660](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/413660)

---

