---
title: "Compilation Issue"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by trunk3d on 2006-08-06
I'm definitely green in respects to Linux. When I try to use the make command I receive the same error, regardless of what I'm trying to compile.
The following text is the error msg received:

make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

I apologize in advance for my ignorance. I have searched high and low for a solution, before ultimately asking for help.
I have the latest GCC libs and appropriate kernel sources. I'm lost here.](*,) 
Thanks in advance for any help offered.

---

### Post by simonn on 2006-08-06
Install linux-headers-[kernel version].

Using synaptic or apt-get etc etc

---

### Post by trunk3d on 2006-08-06
Thanks for the reply simonn.
I have actually already installed those as well. I have seen some forums mention something about a sym link, however none really go in to detail. Based upon your experience, do I need to create a sym link to point to anything in the /usr/src directory etc..?
Thanks again

---

### Post by simonn on 2006-08-07
What does:

```

dpkg -l | grep linux-headers

```

return?

The symlink should have been created by:

linux-headers-2.6.15-26-386 

Is it installed?

---

### Post by trunk3d on 2006-08-07
Thanks for the reply again.
The string returned the following:


ii  linux-headers-2.6.15-26                2.6.15-26.46    Header files related to Linux kernel version
ii  linux-headers-2.6.15-26-386            2.6.15-26.46    Linux kernel headers 2.6.15 on 386
ii  linux-headers-386                      2.6.15.24    Linux kernel headers on 386


Sorry to be such a problem.
(On a side note..my wife was wondering if that's your baby in your avatar. Very cute.)

---

### Post by simonn on 2006-08-07
That seems ok. Weird.

Out of interest, using synaptic find linux-headers-2.6.15-26-386, right click -> properties -> installed files and see if /lib/modules/2.6.15-26-386/build is there.

Also, check to see if /usr/src/linux-headers-2.6.15-26-386 exists. If not, what does live in /usr/src? If so, create the link manually:

```

$ sudo ln -s /usr/src/linux-headers-2.6.15-26-386 /lib/modules/2.6.15-26-386/build 

```

> **trunk3d said:**
> (On a side note..my wife was wondering if that's your baby in your avatar. Very cute.)

It's actually a (very old, and apparently very un-staged) picture of me :).

---

### Post by mlind on 2006-08-07
> **trunk3d said:**
> Thanks for the reply simonn.
I have actually already installed those as well. I have seen some forums mention something about a sym link, however none really go in to detail. Based upon your experience, do I need to create a sym link to point to anything in the /usr/src directory etc..?
Thanks again

Some packages may require that create /usr/src/linux symlink that points to installed kernel headers (in /usr/src)

---

### Post by trunk3d on 2006-08-07
Simonn,
Great news! Manually creating the symlink worked!
But first things first. 
I did as you suggested in synaptic, and the /lib/modules/2.6.15-26-386 
directory was there. 
The linux-headers-2.6.15-26-386 was also there in the /usr/src directory.
I was getting a little bummed until I created the symlink manually as you graciously outlined.
Thank you tremendously for your help. I have learned something new!
I hope that I may return the favor at some point.
P.S. my wife says you were a cute baby,,LOL (she's embarrassed)
Thanks again for teaching me something new.

---

### Post by trunk3d on 2006-08-07
That's exactly what was going on mlind. Thanks for the reply.

---

