---
title: "Wireless not connecting to WPA network - bug report?"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2009-03-24
What info should I include in a bug report? Hardy is connecting fine to the same network so it seems to be a Jaunty bug, unless there's something wrong with my hardware.

---

### Post by Peter09 on 2009-03-25
What hardware have you got
can you post the output of the terminal command

```
lshw -C network
```

---

### Post by nickmcg on 2009-03-25
Is the network failing?
My Jaunty pc cannot resolve host names from the internet, although nslookup works, yet it can resolve local host names.
If I boot from the alpha6 cd everything works as it should.

Nick

---

### Post by QwUo173Hy on 2009-03-25
> **Peter09 said:**
> What hardware have you got
can you post the output of the terminal command

```
lshw -C network
```

Thanks Peter09. I've attached the output of that command. According to lspci I'm using:
Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

I get the two green lights but it never establishes a connection to the router.

---

### Post by Kevbert on 2009-03-25
Please post the output from terminal of
```
iwconfig
```
It may be a sensitivity/noise problem.

---

### Post by Peter09 on 2009-03-25
This appears to be a known problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291685](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291685)

---

### Post by Peter09 on 2009-03-25
Also specific to Jaunty

[http://archives.free.net.ph/message/20090306.130112.a525df19.en.html](http://archives.free.net.ph/message/20090306.130112.a525df19.en.html)

---

### Post by caryb on 2009-03-25
I don't know about wpa but on wep I had to turn off hide ssid on the router to fix my connection.


Cary

---

### Post by QwUo173Hy on 2009-03-25
I've submitted a bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348335). You guys reply quickly!

Thanks Peter09, if those bugs are the same, I'll mark mine as a duplicate.
caryb, I'll try broadcasting the ssid and see if it helps.
Kevbert, I've attched the output of that command.

Thanks so much.

---

