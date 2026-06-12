---
title: "I screwed up username on install"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Whiteeagle on 2008-09-10
I downloaded ubuntu 8.04 yesterday and installed it on 2 PCs. Each has a hard drive used only for ubuntu. 80gigs. 
Yesterday I had trouble booting up. Some kind of error I couldn't understand, on both PCs. Today this PC works fine. The other one still has problems, but I will deal with that one later. 
On this PC Ubuntu went thru setting up the program and got to the sign in Username and password. I only remember setting up the password. I have tried all different ways I would have made an username and I cannot get it to sign in. How do I find out what my username is. I remember the password. 
I am so stoopid.](*,)

---

### Post by maybeway36 on 2008-09-10
Boot in recovery mode and go to a root prompt. Do
```
grep 1000 /etc/passwd
```
This will show you your username. Then reboot with
```
reboot
```

---

### Post by Whiteeagle on 2008-09-10
Thanks maybeway36 I appareciate that help.

---

### Post by Whiteeagle on 2008-09-10
> **maybeway36 said:**
> Boot in recovery mode and go to a root prompt. Do
```
grep 1000 /etc/passwd
```
This will show you your username. Then reboot with
```
reboot
```

Well, I don't know what I did. I found how to boot in the recovery mode and go to a root prompt. I entered the code as you gave me and I got this answer:

root@administrator-desktop:~# grep 1000 /etc/passwd
administrator:x:1000:1000:administrator user,,,:/home/administrator:/bin/bash
root@administrator-desktop:~#

If I had put a username in it would be whiteeagle and maybe some numbers after it (2173) I even tried ,,,:/ as the username in case I did something even weirder than not remembering a username. Thanks for any help.:confused:

---

### Post by Mark Phelps on 2008-09-11
From the results of the grep ...

The name you used was "administrator user".  You can also verify this by seeing that the "user" path has the directory "administrator".

---

### Post by Whiteeagle on 2008-09-11
> **Mark Phelps said:**
> From the results of the grep ...

The name you used was "administrator user".  You can also verify this by seeing that the "user" path has the directory "administrator".

Thanks Mark that was it. 
I told y'all I was stoopid. Really tho, this is my first time using ubuntu in awhile. I installed 7.04 and didn't have any trouble with it at all, even partitioning it. 
That solved my prob on one PC I have.

---

