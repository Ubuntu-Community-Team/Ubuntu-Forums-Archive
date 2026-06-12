---
title: "Anyone testing Evolution. Bug need confirming."
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-10-02
I raised this bug in Jaunty as I've started to use evolution as my only mail client. Have been asked to test in Karmic.
Only one thing is not too good and that is image loading. 

Here's the bug. [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/438841](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/438841)

Can someone confirm it if possible. I have image loading turned off unless email from someone in contacts list, then use View>load images or ctrl i.

---

### Post by philinux on 2009-10-05
anyone?

---

### Post by Technoviking on 2009-10-05
Sorry, working fine for me.

T-V

---

### Post by philinux on 2009-10-05
It's really bad here. If some advertising mail comes through from say amazon. It takes ages for images to download and display.

---

### Post by TrueTom on 2009-10-05
That depends on your definition of slow. It's slow for me for mails that use a lot of inlined images. The problem isn't so much the size of the images as the total count. I'm guessing that Evolution isn't reusing the connection to the host with the images.

---

### Post by TrueTom on 2009-10-05
Ok, I traced the traffic. It does indeed create a new TCP connection for every image including DNS lookup. That takes 250ms for me per image. If an Email has 20 images this takes 5s... :)

---

### Post by Joe_Bishop on 2009-10-05
The first things I do are:
sudo aptitude purge evolution transmission-gtk mono-runtime tsclient vinagre
sudo aptitude install deluge gnote grdc

---

### Post by philinux on 2009-10-05
> **TrueTom said:**
> Ok, I traced the traffic. It does indeed create a new TCP connection for every image including DNS lookup. That takes 250ms for me per image. If an Email has 20 images this takes 5s... :)

Thanks Tom, Could you go to the bug report add your useful comments and change it's status to confirmed.

---

### Post by TrueTom on 2009-10-05
> **philinux said:**
> Thanks Tom, Could you go to the bug report add your useful comments and change it's status to confirmed.

Since this is really an upstream problem I've linked the according bug from bugzilla.gnome.org. Now you just need to fix it... :)

---

### Post by philinux on 2009-10-06
> **TrueTom said:**
> Since this is really an upstream problem I've linked the according bug from bugzilla.gnome.org. Now you just need to fix it... :)

Thanks Tom, bug got triaged now,

Anyone interested this is the bugzilla bug.
[https://bugzilla.gnome.org/show_bug.cgi?id=582591](https://bugzilla.gnome.org/show_bug.cgi?id=582591)

---

