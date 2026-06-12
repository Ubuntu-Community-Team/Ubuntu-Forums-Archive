---
title: "Installing java on Ubuntu 10.04"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by ronyjoe on 2010-10-02
Hi,
   I recently tried installing java onto my OS and also into Firefox, but i'm not being able to do so.
   Please help. Please tell me how to go about with the instructions and how to install the plugin for firefox.
Regards.

---

### Post by lovinglinux on 2010-10-02
Install [ubuntu-restricted-extras](apt:ubuntu-restricted-extras).

---

### Post by ronyjoe on 2010-10-03
I'm sorry but i was asked 2 download an unknown application. Please suggest an alternative to this!!!

---

### Post by krishnandu.sarkar on 2010-10-03
Ya ubuntu-restricted-extras contains many things. It's an one step solution to many problems for new users.

BTW if you want to install only the java plugin for firefox use sudo apt-get install sun-java6-plugin. But make sure to enable Partner repository under System > Administration > Software souces.

---

### Post by lovinglinux on 2010-10-03
> **ronyjoe said:**
> I'm sorry but i was asked 2 download an unknown application. Please suggest an alternative to this!!!

The link above is an apturl, which means the download is pulled from the repositories and not somewhere else on the internet. Is the same as if you went to your Software Center and installed it from there. So, is perfectly safe.

More info about  *ubuntu-restricted-extras* at [http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

---

### Post by ronyjoe on 2010-10-11
I've installed it, but now how do i add it to mozillla firefox???

---

### Post by lovinglinux on 2010-10-11
> **ronyjoe said:**
> I've installed it, but now how do i add it to mozillla firefox???

Is automatic. Java should be listed when you type **about[noparse]:[/noparse]plugins** in Firefox's address bar.

---

