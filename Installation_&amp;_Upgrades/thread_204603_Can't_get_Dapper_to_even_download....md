---
title: "Can't get Dapper to even download..."
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by chopsbuntu on 2006-06-27
I've tried twice now, and this is what I keep getting...
----------------------------

[I]Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found[/I]

-----------------------------
Any suggestions? Also, I am NOT a "beta tester" or anything by any means, so if this Dapper version has a lot of bugs in it, should I even be bothering upgrading to it yet?

My laptop runs rock-solid as is. I don't want things to start crapping out on me and having lock-ups all the time.

Thanks in advance! :-D

---

### Post by taurus on 2006-06-27
You need to edit your /etc/apt/sources.list and comment out the line(s) with [http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/) in it!!!  Then, "sudo apt-get update" to update your list...

---

### Post by chopsbuntu on 2006-06-27
Sorry, but it's been a long time since I've done this stuff. I've just been using Linux, not updating or modifying.

How and where do I do the edit(s) you mentioned?

Again, thanks in advance. ;)

---

### Post by taurus on 2006-06-27
I am assuming you are using a window manager like Gnome.  Open a terminal by clicking Applications -> Accessories -> Terminal.  Then at the prompt, type
```

sudo gedit /etc/apt/sources.list

```

---

### Post by chopsbuntu on 2006-06-27
[QUOTE=taurus]You need to edit your /etc/apt/sources.list and comment out the line(s) with [http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/) in it!!!  Then, "sudo apt-get update" to update your list...[/QUOTE]

Sorry again, but what exactly do you mean by "comment out the line(s)"?

I have the terminal window open and have the list up, but don't know what to do now.

---

### Post by taurus on 2006-06-27
Put a # in front of it!!!

---

### Post by chopsbuntu on 2006-06-27
Go it!! ](*,) 

BTW, I figured it out already and have been back up and running for the last few hours. Thanks anyway. :rolleyes:

---

### Post by bruce89 on 2006-06-27
There should be a button saying "Upgrade to 6.06 LTS" in Update Manager.  See [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

