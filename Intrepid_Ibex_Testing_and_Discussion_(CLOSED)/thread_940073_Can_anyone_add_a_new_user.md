---
title: "Can anyone add a new user?"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by saracen on 2008-10-06
When I try to add a user from the GUI it doesn't work.  It looks as though the account is added but then I can't log in as the new user and when I reopen the Users and Groups tool the account I just added isn't there.

I tried running 'adduser' from the command line and this is what I get:
```
saracen@saracen:~$ sudo adduser test
[sudo] password for saracen: 
Adding user `test' ...
Adding new group `test' (1001) ...
Adding new user `test' (1001) with group `test' ...
Creating home directory `/home/test' ...
Copying files from `/etc/skel' ...
Stopped: symlink: Permission denied

Removing directory `/home/test' ...
Removing user `test' ...
Removing group `test' ...
groupdel: group test does not exist
adduser: `groupdel test' returned error code 6. Exiting.

```Any ideas?  :confused:

---

### Post by taavikko on 2008-10-06
I actuallu just added user via "sudo adduser ubuntu"
which then made me new user.

Did you tried to create new user with existing name?

---

### Post by The_Big_Fish on 2008-10-09
I have the same problem, no matter what I do in the users and groups tool while it looks like its working it will not actually do anything its as if it can't actually save any of the changes it makes :(

also no matter what I do all the users I create with the terminal are stuck with admin permissions

honestly if i cant fix this soon i am going to have to give up on ubuntu :'(

---

### Post by zekopeko on 2008-10-09
why such a pesimist big_fish? report a bug and they will definitely fix this for the final release. why? because it's a blocker/critical bug for sure.

---

### Post by snova on 2008-10-09
It looks like there's a symlink somewhere screwing things up. My guess is it's in /etc/skel, unless it *is* /etc/skel. So run these commands, and post the output, so that we can check for anomalies:

```
ls -ld /etc/skel
ls -Al /etc/skel
```

Since this is in the Intrepid Ibex Testing forum, you're probably using a different version than I am, but I might be able to help anyway.

---

### Post by ajackson on 2008-10-09
> **The_Big_Fish said:**
> honestly if i cant fix this soon i am going to have to give up on ubuntu :'(
If the creation of users on that particular machine is that critical do you really think that you should be using a pre-release version of an OS?

It is good that the problem has been found and hopefully a bug raised but if encountering a bug on a pre-release version of ubuntu is enough to make you give up on ubuntu then you may as well give up on computers altogether as you'll encounter bugs on all operating systems and most applications.

---

### Post by The_Big_Fish on 2008-10-09
thanks guys, i get the following:

```
leo@leo-desktop:~$ ls -ld /etc/skel
drwxr-xr-x 2 root root 4096 2008-06-16 14:44 /etc/skel
leo@leo-desktop:~$ ls -Al /etc/skel
total 12
-rw-r--r-- 1 root root  220 2008-04-15 04:36 .bash_logout
-rw-r--r-- 1 root root 2940 2008-05-12 19:33 .bashrc
lrwxrwxrwx 1 root root   26 2008-06-16 15:16 Examples -> /usr/share/example-content
-rw-r--r-- 1 root root  586 2008-04-15 04:36 .profile

```


> **ajackson said:**
> If the creation of users on that particular machine is that critical do you really think that you should be using a pre-release version of an OS?

It is good that the problem has been found and hopefully a bug raised but if encountering a bug on a pre-release version of ubuntu is enough to make you give up on ubuntu then you may as well give up on computers altogether as you'll encounter bugs on all operating systems and most applications.

i think i might be in the wrong part of the forum, i just used the search to find the same problem i am having. the version of ubuntu i am using is  8.04.1, is this a pre-release version? (i only very recently installed ubuntu for the first time so if i am miss understanding i apologise

---

### Post by philinux on 2008-10-09
If you want you can click the report button on your first post of this thread and ask the mods to move the thread to Absolute Beginners Forum.

---

### Post by snova on 2008-10-09
No, that's the stable version to the best knowledge. Intrepid Ibex is due out in a few weeks, but they're still working on it for now.

Oh, and those instructions were meant for saracen, who appears to be having symlink issues. Nothing looks wrong with yours anyway, fortunately. There is one file there I don't see on my machine, but it's probably just because you have an extra package installed that I don't. Run this to clarify, because I'm curious:

```
dpkg -S /etc/skel/Examples
```

Regardless, the more output you can give, the better. Try running adduser again, The_Big_Fish, and post the output for us. It might not be a related problem.

---

