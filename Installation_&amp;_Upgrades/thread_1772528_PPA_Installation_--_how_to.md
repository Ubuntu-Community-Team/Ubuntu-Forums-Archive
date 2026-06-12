---
title: "PPA Installation -- how to?"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2011-05-31
Hi, all:

Current Ubuntu 11.04 only affords, gdl 2.30.1-1 . However, I really need to have gdl 3.0.0 above, which can be found in launchpad

[https://launchpad.net/ubuntu/+source/gdl/3.0.0-1ubuntu1]("https://launchpad.net/ubuntu/+source/gdl/3.0.0-1ubuntu1")

How can I add this libgdl to /etc/apt/sources.list, so that whenever libgdl is upgraded, info can be easily noticed in Synaptic ? 


Best Regards
Pei

---

### Post by ratcheer on 2011-05-31
Most Launchpad PPA's have a place on the page that says something like PPA Details or Add This PPA. When you click on it, it gives some deb commands. I just copy them into the Software Sources applet. On the Other Software tab, click the Add button, then copy and paste the deb command.

Tim

---

### Post by jiapei100 on 2011-05-31
Are you saying that for libgdl, I'm unlucky enough to have no such kind of "Add This PPA" ? :(
Is it possible that what I wanna install is for Ubuntu 11.10 ?
Oh, yes, let me have a try first....

Rgds
Pei




> **ratcheer said:**
> Most Launchpad PPA's have a place on this page that says something like PPA Details or Add This PPA. When you click on it, it gives some deb commands. I just copy them into the Software Sources applet. On the Other Software tab, click the Add button, then copy and paste the deb command.

Tim

---

### Post by grahammechanical on 2011-05-31
I have just tried to find a PPA for libgdl-3-1 and I keep finding a page that says that it is a part of Gnome 3. Have you installed the PPA for Gnome 3? That should update libgdl as it is developed, should it not?

Regards.

---

### Post by jiapei100 on 2011-05-31
I just added oneiric to my repository source, and everything is working perfect now !! ^_^

Thanks for all of your answers. Thanks ....

> **grahammechanical said:**
> I have just tried to find a PPA for libgdl-3-1 and I keep finding a page that says that it is a part of Gnome 3. Have you installed the PPA for Gnome 3? That should update libgdl as it is developed, should it not?

Regards.

---

