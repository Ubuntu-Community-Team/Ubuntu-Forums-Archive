---
title: "sudo upgrade error"
date: 2016-03-10
forum: MINT
---

### Post by g1nked on 2016-03-10
just installed Mint and very new to linux in general I have been reading and learning forthe last 3 days and I am liking this new OS very much. very open community and very helpful unlike Windows in my experience anyhow.
I was following a tutorial of getting started and when i did sudo get-app upgrade I get this error
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
heman@heman-M11x ~ $ sudo lsof /var/lib/dpkg/loc
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs a
      Output information may be incomplete.
lsof: status error on /var/lib/dpkg/loc: No such file or directory
lsof 4.86
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhKlnNoOPRtUvVX] [+|-c c] [+|-d s] [+D D] [+|-f[gG]] [+|-e s]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]] [-p s]
[+|-r [t]] [-s [p:s]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.
heman@heman-M11x ~ $ 
```

I have read about this error here but not familiar enough to complete without guidance with terminal.
Thanks in advance

```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```
im not afraid to read and learn im just not sure if these terminal commands are right for my scenario. i spent 14 hours on installing Mint over Ubuntu yesterday from a live usb and im afraid of crashing my system. i have alot of computer experience just not much coding and zero Linux knowledge.

also im wondering if i do the sudo apt-get upgrade again in the future what would stop me from ending up in same trouble im in currently if anyone could answer this as well.

Solution 1
```
 sudo rm /var/lib/apt/lists/*
 sudo rm /var/lib/dpkg/lock
 sudo rm /var/cache/apt/archives/lock
```
 i believe this solved my issue

---

### Post by TheFu on 2016-03-11
Welcome to the forums.

Really shouldn't remove locks manually ... er ... ever.    Generally, it means there is another process making use of those files - lock files are a way to prevent multiple processes from modifying a file.  I've never had to remove those files manually in my decades of running Linux.

As for learning Linux, this ( [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) ) is my best advice.  Many Windows skills are counter productive to running Linux efficiently. Best to forget it and come with fresh eyes. Some things appear to be similar on the surface, but they are not. This can be confusing. Took me a few years to learn enough to appreciate *nix architecture, but once I did an entire new world of capabilities opened up.  Things are much easier today, so it shouldn't take as long - plus you are probably smarter than I.

howefield - thanks for added the code tags. Much easier to read.

Ok - onto the error.  I generally would use **sudo lsof |grep lock** to see which processes are locking files. Be less restrictive in your greps / searching.  Filters are a way of life with *nix systems.  Windows can do it too, but very few people use that facility. Plus the shell in Windows isn't as conducive to quick typing and select/paste like bash + X/Windows.

I don't know what **sudo get-app upgrade** is.  Cannot imagine it would work.  Don't have that command here.  Being exact and correct matters, as you know.  Copy/paste is the best way to show commands here. Don't type.

Using **sudo apt-get update && sudo apt-get upgrade** 5000 times shouldn't be an issue.  More than once really shouldn't be required.  The recommendation to do it weekly is my best advice.  [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint)

---

### Post by goofprog on 2016-03-11
It seems like a panic job to me.  I hate it when there are linux application boogers in the last step of the process and prevents future updates.  So the fix is needed.  I guess this is why fedora went from yum to dnf.  Maybe the apt-get utility needs that same solution to prevent installation boogers as I call them.

---

### Post by TheFu on 2016-03-11
There is no panic in the messages posted.  Just normal errors. The programs are working "as designed."

a) The lock file was in use in the first message
b) the lsof command used incorrect options and didn't work in the second and all remaining messages are about that.

                                 **That was all that happened.**  No crash, no program crash, no system panic. Nada.

We don't know how long the OP waited for the lock to become freed.

We don't know if the OP tried killing any "apt" or dpkg related processes. When killed, those should clean up their locks.

We don't know if the OP tried rebooting the box.

We don't know what the syslog or messages or dmesg says. Often there are useful hints in those.

Each of these things really should have cleaned up any lock files, IME.

Most of these commands have a debug or increase verbosity setting/option.  But, since the nuclear option was used (deleting the lock file), we'll never know the root cause - well - until it returns next week or in a few months.

Trying to run apt-get when the APT lock file is exists isn't productive. There is protection for a reason. Please don't ignore it.

Back when I ran Redhat, we used rpm directly and my systems got into "RPM Hell" a few times.  At the time, .deb files and dpkg were the alternative along with slackware's tgz stuff.  They each sucked in their own way.  Since 2002, package management has been pretty great, provided the admin follows best practices and 
* doesn't install packages directly from files. This breaks dependency management and will eventually lead to "DEB hell" or "RPM hell"
* always uses the package manager and lets it manage the dependencies
* if the normal distro repo doesn't have what you need, use a PPA from a reliable, trusted source. PPA software can override distro packages, so it is a dangerous thing.
* the last resort is to load software from source files - these belong in /usr/local/ to keep them away from normal package management. The admin who does this accepts 100% responsibility for configuration, maintenance and updates of these programs.

Anyway - hope that helps.

---

