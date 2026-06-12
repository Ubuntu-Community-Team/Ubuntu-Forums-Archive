---
title: "partitions  between ubuntu and fedora"
date: 2014-03-09
forum: Installation &amp; Upgrades
---

### Post by bhadram on 2014-03-09
I installed dual boot Fedora 19 and Ubuntu 13.10 in the same machine. I  could able to mount the other partitions from both of the OS. I'm  planning to use all the unzipped softwares in Fedora /home/usr/ patition  and use it Ubuntu and viceversa, by editing the env variables. Will it  cause any harm /  damage the file systems as both OS are journaling /  indexing other OS partitions partitions. Are there any side effects of  using other OS partitions in dual boot. Thanks in advance,Please  explain.

---

### Post by ajgreeny on 2014-03-09
> I'm  planning to use all the unzipped softwares in Fedora /home/usr/  partition  and use it in Ubuntu and viceversa, by editing the env variables.I don't fully understand what you mean by this.  You can certainly use all the data files between OSs provided there are no ownership conflicts, but software will be a completely different thing and present you with big problems.

Tell us more please.

---

### Post by buzzingrobot on 2014-03-09
I'll take "/home/usr" to mean your home directories, as in "/home/bhadram".  Otherwise, Linux systems have no "/home/usr" directory.

If by "unzipped" you mean "used the distribution's tools to install software", then those files are located in multiple locations across the file system.  The configuration files specific to you are in your home directory.

However, if "unzipped" means you downloaded a package and unarchived it ( as you might do in Windows ) in your home directory, it will almost certainly not execute. 

What you propose to do with environment variables might, theoretically, work.  But, I'm not sure I see any purpose or advantage, and significant potential downside.   Why not just install what you want to run on each distribution on that distribution? After all, the vast majority of programs on both will differ only in version number, if at all.

---

