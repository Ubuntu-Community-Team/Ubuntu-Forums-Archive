---
title: "/usr/lib/libgconfig2-4/gconf-sanity-check-2 exited with status 256"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by gacosta27 on 2010-09-28
Just got 10.04 LTS. 
Firstly, I have to tell that I got an installation problem, in which I couldn't manage the windows I was working on. I read in other threads that the solution was to create a new user. I did it and my new Ubuntu was working perfectly. 
Now, I turned on my laptop and got a message that says:

init: hwclock main process (282) terminated with status 2
Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored.
root@gaby-laptop:~#

Then I searched for answers in other threads. One of the solutions was to run fsck manually, which I think didn't work. Then I tried mountall start, which led me to the login screen. But before I got to the login box, I got a message box that says:

/usr/lib/libgconfig2-4/gconf-sanity-check-2 exited with status 256

I clicked the only option in the box: Cancel. Then, it appeared a new message that says that GNOME Power Manager did not install correctly, and asked me to contact my system administrator (not other than me). 

The big problem is that I tried to log in from my new account, and it didn't load anything! It just shows the black screen with the pointer on it. 

I NEED HELP ASAP cause I got to do some important homework T.T

---

### Post by gacosta27 on 2010-09-28
BTW... I just noticed there's a difference between my settings time/date and the time that the login screen shows

---

### Post by tomsoms on 2011-01-22
Hi,

I got the same problem, getting:
init: main process (358 ) terminated with status 2.
after a reboot just upgrade from 10.04 to 10.10.

---

