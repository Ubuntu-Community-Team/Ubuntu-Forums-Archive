---
title: "System frozen with screen blanked"
date: 2009-06-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-06-05
Hello, I'm using a laptop with an intel x4500 hd video card (the intel driver might be the cause of the problem).
When I leave the pc alone and I come back after a long time (say 45 minutes) I found the system frozen, with the screen blanked. No way to recover.

Does this happen to any of you?

I would like to file a bug, but I don't know if the cause is either Xorg, the kernel, the intel xorg driver.

---

### Post by Reiger on 2009-06-05
Yup. Since certain Jaunty beta's. Sometimes it doesn't do even as much as going blank and only the touch pad will respond; sometime I get all funky distortions which resolve themselves to a greenish to a blank screen. EDIT: And we are not alone. Ask olskar. ;)

Oh and to add to the treat: since the 2.6.30-8 kernel I get segfaults on boot sometimes...

---

### Post by yelo3 on 2009-06-05
I went back to the -7 kernel and it seems that the problem is gone

---

### Post by binbash on 2009-06-05
I have same issues with *.29 r3 kernel.It was working fine a couple of days ago with same kernel

---

### Post by yelo3 on 2009-06-05
Help if you have my exact issue

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383973](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383973)

---

### Post by geojorg on 2009-06-05
Is because of a screensaver and the power-managment bug wich is related to hal and devicekit, i also have the same problem in mi Dell Inspiron with intel x3100. And I can confirm is only on 2.6.30-8

---

### Post by yelo3 on 2009-06-06
Unfortunately it just happened with -7 too.

---

### Post by geojorg on 2009-06-06
Yo can avoid the bug by setting the screensaver option off. It won't be solve until devicekit is completely working in Karmic, I have updates for devickit today let's hope this one works fine if it does not work i would have to set the screensaver off again.

---

