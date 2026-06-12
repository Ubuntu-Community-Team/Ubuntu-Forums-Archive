---
title: "Postgresql 8.3 becomes inaccessible with upgrade to karmic"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by slowtrain on 2010-01-13
When I recently upgraded my desktop to Karmic, my postgresql 8.3 no longer starts.  I've got data in 8.3 that I need, but now no way to access it.  Karmic upgrades to Postgresql 8.4, but leaves 8.3.  Problem is, I can't seem to start 8.3 no matter what I do (there's no error message.  I even tried removing 8.4 entirely--without effect.

When I try to start 8.3 (using command line or boot-up manager), there is no error message, either in system logs or in the postgresql log file.  There is also no indication of an active postmaster in ps aux or anything listening to postgresql ports in nmap (for that matter, seems there's nothing listening even with 8.4 activated).

I could try to 'upgrade' my data cluster to 8.4.  Never tried that before and am concerned about possibly losing data.  Also, I made a load of tuning adjustments to 8.3 that I'd have to replicate with 8.4.  I'd rather stay with 8.3, if possible.

There are also two pieces of software, postgresql-common and postgresql-client-common, that presumably allow one to run two versions of postgresql simultaneously.  Maybe this stuff is even the source of my start up problems.  No idea where to learn how to use this software, and, esp., whether this would solve the 8.3 start problem.

Thoughts?

---

### Post by slowtrain on 2010-01-13
First, another frustration, and then a solution!

The other frustration:  I tried to update my cluster from 8.3 to 8.4, but it won't let me do so without 8.3 started up.  So, now I'm really in a fix--seems there's no way to get my data back out of 8.3.

Solution:  Turn off 8.4 using something like boot-up manager.  Next, from the command line, issue this:  sudo apt-get install postgresql-8.3 .  This reinstalls 8.3, but doesn't mess with your data.  Now, 8.3 can be started up.  It'll be possible to either continue using 8.3 or update cluster to 8.4.  Ta da!

Complaint:  Here's the bind the 9.10 upgrade puts postgresql users in:  It apparently erases enough of 8.3 so it can't be started, but not so much that a non-expert user can tell, either from command line or boot-up manager, that 8.3 needs to be reinstalled.  Also, when attempting to start 8.3 without a reinstall, there are no error messages to tip the user off that anything is wrong.  In addition, the fact that 8.3 has been partially removed means that data from 8.3 cannot be accessed and the data cluster can't be upgraded to the newly installed 8.4.  This is an unnecessary situation that didn't occur in previous version upgrades.

---

### Post by features on 2010-01-13
Now, I haven't confirmed this, so I could be talking through a hole in my hat, but could it be that postgres 8.3 is listening on port 5433 instead of 5432, when installed alongside 8.4?  

This happened to me a year or two back when they changed from 8.2 to 8.3 - they would install side by side, but 8.3 had the standard port.  we were too lazy to upgrade at the time, so just uninstalled 8.3 (while shaking our fist at the change to implicit casting, but thats a rant for another day)

---

### Post by slowtrain on 2010-01-13
Hey features, thanks for your thoughts!  According to a cluster info command I ran (it's in the install read me), 5432 was still assigned to 8.3 in this upgrade (8.4 got 5433).  In my 2nd msg above, I explain what the actual problem is.  Your msg and my explanation seem to have hit the bboard at just about the same time.

---

### Post by features on 2010-01-13
No worries, glad you got it sorted :)

---

### Post by NicholasLeonard on 2010-02-09
Hi,

I have a similar problem. I just upgraded my system from Jaunty to Karmic. It is a postgres RDBMS. However, after upgrading to 9.10, postgres 8.3 becomes inaccessible. I need to turn it on to pg_upgradecluster my previous installation (or so it seems).

I have tried to apt-get remove 8.3 and 8.4 and then reinstall 8.3 but it always gives me the same issue:
```
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up postgresql-8.3 (8.3.8-1) ...
 * Starting PostgreSQL 8.3 database server                                       * The PostgreSQL server failed to start. Please check the log output.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Their are no messages output to the log. I also tried this:
```
nicholas@gaia:~$ sudo -u postgres /usr/lib/postgresql/8.3/bin/postmaster -D /etc/postgresql/8.3/main
nicholas@gaia:~$ 

```
Which outputs nothing. The postmaster never starts. Its like it never installed or something.

Furthermore, I am using ubuntu server edition 64bit.

Thanks

---

### Post by Fatman_UK on 2010-03-15
Sorry about the double-post, chromium-browser did something strange.

---

### Post by Fatman_UK on 2010-03-15
> **slowtrain said:**
> Complaint:  Here's the bind the 9.10 upgrade puts postgresql users in:  It apparently erases enough of 8.3 so it can't be started, but not so much that a non-expert user can tell, either from command line or boot-up manager, that 8.3 needs to be reinstalled.  Also, when attempting to start 8.3 without a reinstall, there are no error messages to tip the user off that anything is wrong.  In addition, the fact that 8.3 has been partially removed means that data from 8.3 cannot be accessed and the data cluster can't be upgraded to the newly installed 8.4.  This is an unnecessary situation that didn't occur in previous version upgrades.

Agreed, this is horrible behaviour. My Jabber server suddenly started refusing logins, which eventually I traced back to this issue. I'll issue a bug report with the package maintainer, soon as I find out who it is.

[EDIT]

BTW, I can confirm that "sudo aptitude remove postgresql-8.4" followed by "sudo aptitude install postgresql-8.3" works a treat for restoring the database. Thanks slowtrain.

[EDIT]

Bug reported.
[https://bugs.launchpad.net/ubuntu/+source/postgresql-8.4/+bug/538995](https://bugs.launchpad.net/ubuntu/+source/postgresql-8.4/+bug/538995)

---

### Post by jusaf on 2010-05-08
hi!

we are having the same problem, 8.3 will not start anymore and does not output any error.
 we tried your solution already, but somehow 8.4 still remains there, and 8.3 is still unable to start.

we managed to remove 8.4 but no luck with getting 8.3 back up, this is the output every time:

```
root@sql1:~# /etc/init.d/postgresql-8.3 start
* Starting PostgreSQL 8.3 database server
* The PostgreSQL server failed to start. Please check the log output.

```

any idea how to solve this?
We have very important data in 8.3 and we are already offline for 20hours... :(

thanks in advance!

---

