---
title: "what is the default root password on new Hardy Heron?"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by sptrsn on 2010-02-17
Could someone tell me what the default root password is on a brand new Hardy Heron install?
I'm clueless.
Thanks.

---

### Post by zellfaze on 2010-02-17
I'm not sure anyone would know.

My recommendation:

[list][*]Login to your account
[*]Load a terminal
[*]Type *sudo -i* This will log you in as root.
[*]Change the root password.[/list]

Now you have the root password.

---

### Post by meierfra. on 2010-02-17
In  Ubuntu  the root account is disabled:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sptrsn on 2010-02-17
So does the user I created during install have root privelages?
That article helped meierfra. thanks.

The reason I ask is that I tried to ssh into the server following these instructions...
[http://nanotux.com/blog/the-ultimate-server/](http://nanotux.com/blog/the-ultimate-server/)
and was challenged for the root password. 
I've wiggled my way through it, but am still kind of confused. On my other machine I must have created the root password. I just don't remember. I'll try that. thanks zellfaze.

---

### Post by meierfra. on 2010-02-17
Yes. Via "sudo"

---

### Post by Sef on 2010-02-17
Read [**Forum policy on log-in-as-root tutorials.**]("http://ubuntuforums.org/Forum%20policy%20on%20log-in-as-root%20tutorials")

---

