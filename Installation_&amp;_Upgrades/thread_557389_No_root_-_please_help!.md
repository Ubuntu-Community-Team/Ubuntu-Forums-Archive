---
title: "No root - please help!"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by MiD-AwE on 2007-09-22
Please help!

I recently had to reinstall Ubuntu 7.04 due to grub issue with XP/vista boot manager. I thought that I was being clever when I mounted my old /HOME from seperate partition, but after fresh install now I can log in but my account hangs without displaying any menus. So, I have also the option to login to my wife's account but I'm denied any root access.

How can I either get root access anyway in my wife's account or reset my account to the default desktop. I love to customize my desktop and I imagine that something I did to my account is preventing it to restore. My wife always likes to keep the desktop simple and that is probably why I can still log in as her without root.

I have a friend stopping by tonight and I want to show off Ubuntu (trying to convince him to install/make the switch from windows.)

When I say I have no root from her account, I mean I have no access to synaptic. I tried to reinstall automatix2 but it wont accept her password to allow any installation.

Thanks in advance, I'm still somewhat new to Linux, having made the switch back with breezy. This is the first crippling issue I've ever faced.:confused:

---

### Post by sisco311 on 2007-09-22
>  How can I either get root access anyway in my wife's accountreboot and select recovery mode from the grub menu
```


addgroup your_wife's_user_name admin


```

---

### Post by aysiu on 2007-09-22
What sisco311 said. More details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by MiD-AwE on 2007-09-22
Thanks, I've gotta log off to give this a try. BRB.

---

### Post by MiD-AwE on 2007-09-22
Sorry, this didn't work.

The error said, "user admin does not exist"

What's next?

Should I just reinstall Ubuntu again doing something differently? Is it even possible to merge-or-mount two or more /home directories?

---

### Post by sisco311 on 2007-09-22
sorry it's:
```
addgroup your_wife's_user_name admin
```

---

### Post by MiD-AwE on 2007-09-22
Thanks, I was reading [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) and just saw that.

Ok, so here I go again. BRB.

---

### Post by MiD-AwE on 2007-09-22
Thank you sisco311 & aysiu.

Worked like a charm. I'm installing Ubuntu updates as I type. I suppose the next step is to delete my account and then set it up again as new? Any advice or cautions?

***
A little advice to others who may read this, I have started a journal about a year ago for jotting in these helpful tidbits. I just made a new entry with this information. I used to bookmark this kind of information but found that it didn't help if I was unable to access my personal files. The journal is essential since it is written in my own hand and I know that these things work on issues that I may never see again. (My best advice for new Ubuntu users)!
***

---

### Post by mikewhatever on 2007-09-22
> Should I just reinstall Ubuntu again doing something differently? Is it even possible to merge-or-mount two or more /home directories?

Sounds like a bad idea. Why is it necessary?

---

### Post by MiD-AwE on 2007-09-22
> Sounds like a bad idea. Why is it necessary?No it's no longer an option everything is good. The fix worked and I'm working on the next problem of getting my own account up again.

---

