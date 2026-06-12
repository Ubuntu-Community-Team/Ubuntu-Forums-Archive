---
title: "Fresh Install to 10.10;  Partition for /home"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by wannabegeek on 2011-07-19
Hi all,

I just did a fresh install  from 9.10 to  10.10 and this time I made a partition for my /home .

To accomplish this /home partition thing, I edited fstab to mount the physical parition containing my old /home from 9.10  (by UUID), to /home under 10.10.
 
So far most everything is working well.

However, scripts in my /home/bin directory are working. My .profile file hasn't been modified, and still contains the lines to add /home/bin to my PATH variable.

Also,  FF 3.6.18  has some mouse/cursor lag issues sometimes.

I have never used a separate partition for /home before, so I suspect there are some conflicts occuring.

Any specific info. on these issues would be great, or if you have some general wisdom about using a separate /home partition and upgrading, that would help too.

tia,
wbg

---

### Post by bodhi.zazen on 2011-07-19
Hard to know if your problems are related to your shared home or not.

Did you create a new user with a unique name, or, as I suspect, are you using the same user name ?

In general, I advise a unique user name with each distro / release on a shared home.

In general, sharing a home directory across distros / releases will work without any problem, but not always.

To test if it a problem with your old home, simply make a new test user. If the problem persists across users, it is a system problem, if no, a config file in your shared /home.

---

### Post by wannabegeek on 2011-07-19
Thanks bodhi,

I tried to log in as another user I had created. I got s bunch of error messages that nautilus couldn't create the various home
directories for this other user. 

I did delete the old home directory created when I installed 10.10.

EDIT: I did not create a new user name as you suspected in your response either. And,  on this fresh install, I made a new password. When I boot, I get asked for a keyring
password (from network manager I think), since my master password is not the same as the keyword.

---

### Post by wannabegeek on 2011-07-20
Dumb mistake...I was trying to use a script which worked differently than I thought.... 

No issues with new /home partition and /bin

---

