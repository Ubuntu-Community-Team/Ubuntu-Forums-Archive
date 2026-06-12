---
title: "lost wireless after upgrading to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by proteanthread on 2011-10-14
It appears that the upgrade to Kubuntu 11.10 went flawlessly except for one thing:

I lost access to my wireless adapter and the ability to logon to my network.

Looks like the upgrade changed some permissions, am I correct? What would I need to do to get my wireless back up? :confused:

---

### Post by mohansathish on 2011-10-14
Hi, 

Are you accessing the adapter from the time of startup?
If so, and you are getting some errors like “Booting system without full network configuration”, then you have to check the new whether FHS got updated in your machine.  

Check and do if you do not have it


[LIST=1]
[*]Create directories /run and /run/lock
[*]Move contents of /var/run into /run and /var/lock into /run/lock
[*]Delete directories /var/run and /var/lock
[*]Create replacement simlinks
[*]Reboot your machine
[/LIST]

Reply if you already have /run and other folders and contents

----
Please mark the thread as solved once you have got the solution
Click me: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by proteanthread on 2011-10-14
How do I create replacement symlinks?

---

### Post by mohansathish on 2011-10-14
I can show examples

[INDENT]ln -s /run /var/run
 ln -s /run/lock /var/lock


[/INDENT]Just make an update it will work.

---

### Post by proteanthread on 2011-10-14
I already have /run/lock and /var/run/lock so i just move everything into them?

---

### Post by mohansathish on 2011-10-14
Yes, Go ahead.

---

### Post by coryjsanders on 2011-10-21
Hi,  I am new to Kubuntu.  I lost my wireless on upgrade, too.  
I have the following: 
/run with contents
/run/lock with no contents
/var/run with contents
/var/run/lock with no contents
/var/lock with no contents

Can you advise me?  Thanks.

---

