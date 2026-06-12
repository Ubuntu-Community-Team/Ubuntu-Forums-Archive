---
title: "Updates not working in Ubuntu 7.04"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by patrick87 on 2007-04-19
I tried installing 2 updates, and one restricted driver right after install. My internet obviously works. I am posting this. I went to terminal and tried "sudo apt-get update" and it gave me this

gecko@gecko-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
gecko@gecko-laptop:~$ 


is it just the ubuntu server is hosed up with so many ppl trying to update and stuff right now?

That is what i was just thinking it was. I hope it is nothing serious anyway....

i also thought i might be my sources.list...  possibility?

Thanks in advanced for any help.

---

### Post by djails on 2007-04-20
Try running 
```
lsof /var/lib/apt/lists/lock
```
to see which process is currently holding the lock on the lockfile and try to kill it

---

### Post by martijn hoekstra on 2007-04-20
```
martijn@martijn-desktop:~$ lsof /var/lib/apt/lists/lock 
martijn@martijn-desktop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
martijn@martijn-desktop:~$ 

```

:/

---

### Post by macozz on 2007-04-22
Same problem here... I am worry about not having updates, quite common in the first days of a release...
Any solution out there?

P.S. An apparent solutin is here ([https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/101926)](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/101926)). It consist in just deleting the lock file in /var/lib/apt/lists/. All seems to work now... Even if no updates appeared... Strange...

---

