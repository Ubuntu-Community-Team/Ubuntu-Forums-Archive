---
title: "running process as root on startup"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by vanderkerkoff on 2008-01-16
how do I go about this guys

I need to start nginx as root user from a script without entering the password all the time.

Here's the line in the script

sudo killall nginx; sudo /usr/sbin/nginx -c /www/django/django_projects/conf/nginx.conf

I use the script to restart all of my django sites as I'm developing on them.

any ideas?

I'll also need to run it at boot once I'm finished, so I"m guessing I can copy the entire thing into rc.local, or call it from there, and then set the processes that run as non boot user with su -c username "command" and remove the sudo from the root processes.

Anyone?

Thanks in advance.

---

### Post by Keith Hedger on 2008-01-16
This may not be very secure but you can use:```
echo YOURSUDOPASSWORD | sudo -S COMMANDTOBERUNASSUDO
```

---

### Post by vanderkerkoff on 2008-01-17
Thanks Keith that worked a treat.

What are the security implications other than having the password written in a file somewhere?

If the area the file is in is secure then it's pretty much OK isn't it?

Thanks again

---

### Post by Keith Hedger on 2008-01-17
Well its never a good idea to leave your password hanging around in clear text,but as you say if you are on a secure machine it shouldnt be too much of a problem.
Also about the second part of your question yes copy the script to /etc/init.d and make a symlink to it from one of /etc/rcX.d where X is the run level if you look at the scripts its fairly obvious how they work, and you can get rid of the sudo when you install the script as the init scripts are run as root (at least rc0.d is as i use this myself).

---

### Post by vanderkerkoff on 2008-01-17
Cheers Keith

Is it okay to use rc.local?

matt

---

### Post by Keith Hedger on 2008-01-17
just had a look at /etc/rc.local and the way its worded it is run at every time the run level is changed which may mean that your script is run multiple times which is probably not what you want, so i would personally avoid it as the system itself doesnt seem to use it, of course i could be wrong you can always "suck it and see"

---

### Post by vanderkerkoff on 2008-01-17
Hi Keith

just had a look at /etc/rc.local and the way its worded it is run at every time the run level is changed


I am using this method on one server we've got to kick off web apps, they are only running the one time so I"m not certain that on boot the run levels are changed.

Or maybe rc.local is run every time the run levels change, and the run levels do change on boot but all the proccesses that are started in one run level are shut down nicely before the new ones start?

Not sure myself, suck it and see sounds about right 

:-)

Thanks Keith

---

### Post by Keith Hedger on 2008-01-17
Yeah it makes sense that services are only started once during bootup but i'm pretty sure the run level does change, well we both learned somthing :) have fun!

---

