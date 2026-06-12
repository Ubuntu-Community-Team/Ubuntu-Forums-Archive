---
title: "Virtualization in 8.10?"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jstalin on 2008-09-12
I upgraded to the 8.10 Alpha 5 and it killed my virtualbox. Is there any alternate virtualization software available that works in 8.10?

---

### Post by overdrank on 2008-09-12
Hi and welcome, moved to Intrepid Ibex Testing and Discussion  :)

---

### Post by BlueSkyNIS on 2008-09-12
Reinstall VirtualBox, that should help it.

---

### Post by jstalin on 2008-09-12
OMG, I feel like such a n00b. That did it. Thanks! :)

---

### Post by Quadchris on 2008-09-12
You can also use

virtualbox from sun repository

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

see the how-to on their site :

[http://virtualbox.org/wiki/Linux_Downloads](http://virtualbox.org/wiki/Linux_Downloads)

It works out of the box for hardy or intrepid with dkms.

You can also used the package "virtualbox-2.0" which is the newest version.

amd64 and i386 arch are available.

---

### Post by xebian on 2008-09-12
> **jstalin said:**
> OMG, I feel like such a n00b. That did it. Thanks! :)

Reinstalling is not the answer.  You just have to recompile the kernel modules for your specific kernel.  Once you have the particular kernel running, execute this command
```

sudo /etc/init.d/vboxdrv setup

```

Everytime you install a new kernel, you have to do this again.

---

### Post by BlueSkyNIS on 2008-09-12
> **xebian said:**
> Reinstalling is not the answer.  You just have to recompile the kernel modules for your specific kernel.  Once you have the particular kernel running, execute this command
```

sudo /etc/init.d/vboxdrv setup

```

Everytime you install a new kernel, you have to do this again.

But it get's the job done.

---

### Post by forumache on 2008-09-15
> **BlueSkyNIS said:**
> But it get's the job done.

listen to xebian when he/she says that reinstallation of virtualbox is not the answer and the good answer is sudo /etc/init.d/vboxdrv setup.

you are right too, it get's the job done, but the good answer is the one where you understand what was wrong.

after all, reinstalling Ubuntu would have "fixed" the problem too... but this is not Windows, you don't reinstall it, you *fix* the problems.

enjoy.

---

### Post by BlueSkyNIS on 2008-09-15
In my case > sudo /etc/init.d/vboxdrv setup didn't helped.

---

### Post by inportb on 2008-09-15
Then you obviously had a different case.

If the kernel module needs rebuilding, the GUI would say so.

---

### Post by BlueSkyNIS on 2008-09-16
ohhh, I find the error...I didn't typed **sudo** when issuing the commands.

My bad, sorry :(

---

