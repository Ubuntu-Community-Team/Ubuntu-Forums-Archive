---
title: "Need help with installing..etc"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by tokkos on 2006-09-12
Ok i was given a task to install a Ubuntu Dapper Drake 6.06 server(no graphic user-interface) in school and need some help.

so far ive installed:
-Apache2
-Php5
-MySQL
-SSH
-SAMBA
-DNS

The following things are what i still need and have been looking for info/help for days.

-Need to install PhpBB and Wordpress(or something similar)
but i cant find out how to do this since "sudo apt-get install phpbb" doesnt work :D 

-Need to create 5 users and im not sure if "sudo adduser name" works?

-Need to somehow make the server take a backup each night of the MySQL files on it.Backup should be sent to /home/backups.

-Also this isnt important but how do i upgrade it so it has a graphic user-interface? What do i need?


Please help ive been trying to find the right answers for ages now.

Thanks.

---

### Post by Jussi Kukkonen on 2006-09-12
> Need to install PhpBB and Wordpress(or something similar)
but i cant find out how to do this since "sudo apt-get install phpbb" doesnt work
apt-cache search phpbb
apt-cache search wordpress
> -Need to create 5 users and im not sure if "sudo adduser name" works?
According experience and *man adduser*, it should. I believe you should try...
> -Need to somehow make the server take a backup each night of the MySQL files on it.Backup should be sent to /home/backups.
More information is needed here, can you describe the problem more? -- e.g. do you mean you just want files sent to another machine? In that case rsync might be your tool. There must be some mysql-backup tools too, asking/searching at a mysql forum might work...

> -Also this isnt important but how do i upgrade it so it has a graphic user-interface? What do i need?

Installing ubuntu-desktop should do it.

> Please help ive been trying to find the right answers for ages now.

No offence intended, but that does sound like a pretty big exaggeration. The backup problem is the only tricky thing in the list (if you want to do it right), the rest should be answered pretty easily by searching the forums or the wiki, using apt-cache/synaptic/packages.ubuntu.com or man pages...

There's nothing wrong with asking questions though, especially when you're installing internet-facing software like phpbb (which btw doesn't exactly have a stellar security record -- pay attention to the configs).

---

