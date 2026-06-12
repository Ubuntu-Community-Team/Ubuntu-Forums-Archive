---
title: "installing a software for all users"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by 2ndofaug on 2010-08-02
Hello

I am trying to install a software that could be accessed by all users instead of using the whole path "/home/user/dir/software" I would simply like to make it "software" without the ./ at the begining , I googled alot and even searched the forum I am sure someone already asked this before but maybe the search term I used did not match

excuse my english and thank you all

---

### Post by viralmeme on 2010-08-02
> **2ndofaug said:**
> I am trying to install a software that could be accessed by all users

What's the name of this software ?

> **2ndofaug said:**
> instead of using the whole path "/home/user/dir/software" I would simply like to make it "software"

You can specify the full path to the software with the environmental variable $PATH as defined in /etc/profile.

---

### Post by 2ndofaug on 2010-08-02
> **viralmeme said:**
> What's the name of this software ?

john the ripper, i downloaded the latest which i didnt find in the repo and I want it to function as if I installed it from a repo where all users can simply type "john etc..."

You can specify the full path to the software with the environmental variable $PATH as defined in /etc/profile.

you mean as a bash alias ?

---

### Post by viralmeme on 2010-08-02
> **2ndofaug said:**
> you mean as a bash alias ?
Add export PATH=$PATH:/path/to/software to /etc/profile

What's the name of this software ?

---

