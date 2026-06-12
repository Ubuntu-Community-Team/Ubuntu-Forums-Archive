---
title: "MySQL data on single separate partition, used by Ubuntu 18.04 OR 20.04"
date: 2021-10-29
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2021-10-29
I started to write a post about problems, but I’ve realized that although the result I’m trying to achieve is the same, the way to get there might be different than the way I’ve tried.

Objective: Single set of MySQL data (and other relevant files), that two different Ubuntu versions on the same machine can use, but not at the same time.

The tutorials I’ve been using are about moving the data to a different place, which is what I’ve been doing for other parts of migrating from 18.04 to 20.04.  I have a dedicated partition for mount point /data.   I believe this will help me move to 22.04 more easily and quickly.  I’ve discussed this in a different thread, and will update that as things progress farther. But I think this is a separate topic.

I don’t want to write much about what I already tried with MySql because it backfired. I was stuck with nothing working, and I’ve only just recovered it.   If doing what I want is too time consuming, and there is a quick way to move to 20.04 quickly, and then later do it correctly, that might be worth it.

Now that I’ve looked and thought more, it seems possible that what’s holding me back is MySql version differences and ramifications, but I don’t want to assume that without seeking advice because I might cause more problems.

For the 18.04 system, "mysql -V" generates:
[FONT=Courier New]mysql  Ver 14.14 Distrib 5.7.35, for Linux (x86_64) using  EditLine wrapper[/FONT]


and for the 20.04 system, "mysql -V" generates:
[FONT=Courier New]mysql  Ver 8.0.27-0ubuntu0.20.04.1 for Linux on x86_64 ((Ubuntu))[/FONT]

The 20.04 output makes pretty good sense to me.  MySql version 8.0.27, installed on the clean Ubuntu 20.04 installation.  MySql was installed with the LAMP server using tasksel on a desktop OS version.

The 18.04 output is more confusing.  I can see MySql 5.7.35.  I  thought the MySql installation was part of my LAMP install on top of Ubuntu desktop – that’s what I’ve done for a while.  Perhaps the other parts are something to do with porting MySql from an older OS.

Question #1.   Can I upgrade from MySql version 5.7.35 to 8.0.27 on the 18.04 OS?  Is that fairly easy?  I’ve read information about incompatibilities that might explain some of the issues I encountered.  Good backups are obviously important.

Question #2.  Is my objective of putting the data on a separate partition accessible from either 18.04 _**or**_ 20.04 realistic? Will using one OS version and then a different one mess up the data or configurations?  I don’t expect to keep both OS versions in use for long unless I run into other issues with software.  I’ll plan on doing the same thing again after 22.04 is released.  In broad terms, there will be a common /var/lib/mysql directory on the /data partition with a symbolic link to it from /var/lib/mysql on each OS partition.  Having played with the files, I’m not sure there is any need to change the /etc/mysql/mysql.conf.d/mysqld.cnf file or the /etc/apparmor.d/tunables/alias file (or any benefit).  Is it a good idea to centralize log files?

Question #3.  I’m guessing that if I do switch to a different OS version (even temporarily) it would be smart to make sure that the MySql versions between the OS versions are consistent.  And any configuration changes are also consistent or centralized.  Does this make sense?

Thanks!

---

### Post by TheFu on 2021-10-30
Mixing versions of a program to access the same data files, especially DBMS, is dangerous to the data.  There could be issues in how things are written to those files internally which would lead to corruption.

Now, if you only access the files using exactly the same version of the program, that should work. Whether the exact same version is possible on two different OS releases is a different question.  I wouldn't try it - I'd upgrade to whatever the newer release supports.

Regardless, I'd have excellent backups, perhaps multiple backups of the data created every few hours to mitigate some risks with corruption.

Why not just run the DBMS in a single container/VM and access it from each other OS over the network?  Then you can access it from 18.04, 20.04 and 22.04 as needed.  Also, when you are ready to migrate the DBMS from 18 --> 20 --> 22, you have just that DBMS VM to deal with, not the other aspects of the system(s).

Virtual machines solve lots of issues. Use the tools available.

---

### Post by 5circles on 2021-10-30
Thanks @TheFu, for very helpful advice.

Because I'm short of time with a project that has almost zero dependence on the OS move, I'm sticking with 18.04 for at least the next few days.   I just used grub-customizer to set up 18.04 as the default.

The virtual machine idea is intriguing.  I haven't yet pulled a dedicated Linux laptop out of storage after moving. There's also a windows machine with VMs, that needs time with support for the windows base. Either might solve the problem of avoiding sitting on a branch that you are cutting off - in a different way.

---

### Post by MAFoElffen on 2021-10-31
TheFu's answer is more elegant and makes sense in a short time period... On long-term if it would not be mixed Verions of releases. You are somewhere in between that.

If mixed versions, it would be either a locked downgrade to those on 20.04, or an upscaled upgrade to those on 18.04, to ensure all were on the same version of DBMSclient. What dictates which way that needs to be, is the version of the DBMS database itself. That should dictate what should connect to it 'correctly'.

Doing mixed versions of OS released and changing the connection of DMBS client versions to conform to connecting to a specific DBMS version is actually more complicated than what TheFu suggested. But it is possible each way.

Are they connecting directly to the DBMS Service by connection strings? Or through another application, which it's connections strings? And is there any specific version release differences in those? (See how that can get more complicated fast?)

---

