---
title: "Ubuntu-Desktop package doesn't exist!"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by tojikyoto on 2006-08-01
So... I installed kubuntu this afternoon for the nth time after switching back and forth between XP, OS X, and Ubuntu.

As per usual habit, I find the Kubuntu install disk to be more stable on my machine so I use it and then switch to gnome.

That didn't work this time though!!!

```
***@mobile:~$ sudo -i
password:***
root@mobile:~# aptitude update
// blah blah blah done.
root@mobile:~# aptitude install ubuntu-desktop
// blahs... done reading list, building dependency tree, etc.
Couldn't find package "ubuntu-desktop". However the following... 
// tells me there's kubuntu-desktop, which I'm running
```

So I've updated, I also uncommented all the repositories.

Why isn't it there!?!?! ](*,)

---

### Post by aysiu on 2006-08-01
Can you post the output of this command? ```
cat /etc/apt/sources.list
``` Also, instead of saying > blah blah blah done, can you post the actual output of ```
sudo aptitude update
```?

---

### Post by tojikyoto on 2006-08-01
Yea, I found the issue.

As I nano'd the sources.list I found that I had missed the two restricted repositories - but had gotten all the rest. So I fixed that and I'm in the middle of switching my laptop to Gnome as I type.

Thanks.

---

