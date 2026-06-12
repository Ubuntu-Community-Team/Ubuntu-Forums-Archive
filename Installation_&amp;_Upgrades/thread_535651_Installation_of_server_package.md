---
title: "Installation of server package"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by shellte on 2007-08-26
Hi, guys

  I now have a new Ubuntu 7 server and plan to install some server package such as Radius and Web and sth. 

  But I don't have CDROM at all so when I try "sudo apt-get install xxx" there I was asked to insert Ubuntu server CD. 

  So is there any method can complete the installation without CD?

  Thanks.

---

### Post by merlinus on 2007-08-26
System/Administration/Software Sources.

Uncheck cd.

-merlin

---

### Post by shellte on 2007-08-26
Thanks for your help merlin.

But unfortunitaly I can't use x-windows coz it is the server version so no graphic interface is available.

Any suggesttion?

Thx.

---

### Post by merlinus on 2007-08-26
```

sudo nano /etc/apt/sources.list

```

Delete any lines referencing your cd.

nano is a text editor.  If not installed, try vi.

-merlin

---

### Post by shellte on 2007-08-26
Oh, It works.

You really helped, my friend.

Thanks so much!

---

### Post by merlinus on 2007-08-26
You are most welcome!  Glad it worked, and post back with any other issues.

-merlin

---

