---
title: "synaptic package manager"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by animeh on 2008-02-10
When I start the SYNAPTIC PACKAGE MANAGER it loads for one second and then closes before it loads the list.

Does anyone have any ideas what might have happen and what I can do to fix it?

---

### Post by Partyboi2 on 2008-02-10
Open a terminal (Applications>Accessories>Terminal) and type
synaptic and see what messages you get.

---

### Post by animeh on 2008-02-10
I was able to open a terminal and type "Synaptic" and got a messge of the following: 

Starting without administrative privileges

---

### Post by animeh on 2008-02-10
then I got another message: 

Segmentation fault (core dumped)

---

### Post by Partyboi2 on 2008-02-11
maybe the work around [here ]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/72475")might work

---

### Post by animeh on 2008-02-11
the link that you gave me I thought about it and it turns out to be that I only need to type the following:

Sudo apt-get update [enter]

and it scrolled through some things and then I ran the Synaptic Package Manager and it worked. 

Thank You very much Partyboi2

---

