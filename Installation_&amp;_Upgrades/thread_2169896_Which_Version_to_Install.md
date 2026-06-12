---
title: "Which Version to Install"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by borgward on 2013-08-23
I recently was given a dead Dell Latitude D600. Celeron. 500MB RAM. 32 bit. Replaced the HDD.

I tried Installing Ubuntu 10.04 as well as several versions of Mint. Mint said it would not work w/the processor. Mint was supposedly 32 bit. I finally ran Ubuntu 5.10 live. That worked pretty well. I do have the 5.10 Install disk. What's the latest version of Ubuntu that will work with the Latitude.

---

### Post by ibjsb4 on 2013-08-23
What you want to run is too old.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by borgward on 2013-08-23
Too Old? You mean the Latitude or Ubuntu 5.10?

---

### Post by SweetAurora on 2013-08-23
Try very lightweight Linux Distros. Like Lubuntu, Crunchbang, Puppy Linux, DSL (Damn Small Linux). They are usually easy to use!

---

### Post by ibjsb4 on 2013-08-24
> **borgward said:**
> Too Old? You mean the Latitude or Ubuntu 5.10?

5.10, check that link out :)

---

### Post by deadflowr on 2013-08-24
Define what you mean by dead?

What was wrong with the machine to be called dead?

---

### Post by borgward on 2013-08-24
Hard Drive was bad.

---

### Post by grahammechanical on 2013-08-24
When we use a CPU that old there is another issue other than 32 bit or 64 bit and that is, does the CPU support PAE? If the OS is looking for a CPU that sopports PAE and does not find one it will not install. So, we need to use a version of the OS that has a non-PAE kernel. This I guess is the main reason the 10.04 and Mint will not try to install.

This link will help you understand what I am saying and how to get an up to date version that has a non-pae kernel. How well they will run on that machine, who can say?

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Regards.

---

