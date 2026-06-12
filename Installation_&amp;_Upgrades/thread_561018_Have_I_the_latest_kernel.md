---
title: "Have I the latest kernel?"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by outstandish on 2007-09-27
I'm using dapper 6.06 lts  and update manager for simplicity.

uname -a 
gives
 2.6.15-29-386 #1 PREEMPT Wed Aug 29 13:20:33 UTC 2007 i686 GNU/Linux

and
:~$ apt-cache search linux-source- --names-only
gives
linux-source-2.6.15 - Linux kernel source for version 2.6.15 with Ubuntu patches

I'm doing this because my update manager showed I need a newer kernel, but it and synaptic won't run anymore.8-[8-[8-[8-[8-[8-[

If I am running the latest kernel I will post again asking for help on update manager, otherwise I would appreciate pointers to fixing my system with apt.
8)

---

### Post by Sef on 2007-09-27
Does synaptic give you a message?

---

### Post by outstandish on 2007-09-27
No, It shows "starting administrative application" in the info bar, but then that just dissapears.:confused:

---

### Post by outstandish on 2007-09-27
Replying to my own post..
OK I think I've solved my problem.
I realized that just because update manager had told me what was needed it didn't mean that an apt-get update had been done. On trying this I got the message to the effect that could not locate <mymachine> by gethostbyname().
I had had this before with a corrupted hosts file and this time it looks as though the hostname had been deleted after "127.0.0.1 local host"
so changing this to 127.0.0.1 localhost <mymachine> fixed it. 
Any comments on this welcome.
Also whether changing the line in host.conf that reads "multi on" to 
multi off
would be a good idea (I do have a very large hosts file).
Must go now...:)

---

