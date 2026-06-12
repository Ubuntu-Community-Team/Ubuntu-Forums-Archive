---
title: "Cannot update/cannot remove corrupted file"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by ellenjulia on 2011-06-15
I've been running Ubuntu 10.10 for a while now, and until recently, it was running perfectly. Then all of a sudden, I can't install updates. I consistently get the same error message: 

(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `linux-headers-2.6.35-25-generic': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

After a bunch of poking around, I managed to find and have followed most of the advice in [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/145648](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/145648) which seems to be for a similar problem. 

So now my problem is that when I try to run
ellen@ellen-laptop:~$ sudo rm -r var/lib/dpkg/info/linux-headers-2.6.35-22-generic.list

I get 
rm: cannot remove `var/lib/dpkg/info/linux-headers-2.6.35-22-generic.list': No such file or directory

Even though I can go find the file myself. It will not open though. 

I'm pretty sure this file is corrupted and I want to delete it, but other than the remove command, which isn't working, I don't know how to do that. 

Any help or suggestions greatly appreciated.

---

