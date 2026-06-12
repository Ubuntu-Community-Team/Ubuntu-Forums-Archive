---
title: "Cannot Remove Lighttpd Package"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Paerez on 2006-06-02
Hello all, I am having trouble removing lighttpd:

```

(Reading database ... 81366 files and directories currently installed.)
Removing lighttpd ...
 * Stopping web server lighttpd                                          [fail]
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing lighttpd (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting web server lighttpd                                          [ ok ]
Errors were encountered while processing:
 lighttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

as you can see it seems to be the stopping of the process that is causing the trouble. The same thing happens when I run:
```
$ sudo /etc/init.d/lighttpd stop
```
It says OK to start, but Fail to stop.

Also, a "ps aux | grep lighttpd" reveals that it is not running, and there is nothing in /var/lock that I could find. So how do I remove it?

---

### Post by Paerez on 2006-06-15
I fixed it by re-installing and then removing. Silly me. I tried this after messing with the /etc/init.d/lighttpd and the /etc/lighttpd/lighttpd.conf to the point where it wouldn't start... ah well.

---

### Post by Alucard_swe on 2006-06-28
Having the same problem, but reinstalling it dont work for me.
can´t stop it!

---

### Post by Paerez on 2006-06-28
could you perhaps.... elaborate?

---

### Post by cnu on 2006-07-08
I too had installed lighttpd and now cannot remove it. I want apache2 to be installed instead. 
Any pointers on how to do it?

---

### Post by Paerez on 2006-07-10
All I had to do was go into synaptic and mark lighttpd for reinstallation. Then apply, then mark for removal, then apply.

---

### Post by ojintoad on 2006-07-19
I am having the same problem.  This is extremely disconcerting and I really wish there was a good explanation.

I'd be willing to look in log files if someone could inform me where to look.  But the automated process is just making it hard to know what's going wrong.

---

### Post by Paerez on 2006-07-19
if you type:
```
sudo apt-get remove lighttpd
```
you will get the full output in the terminal.

---

### Post by RoadWarriorEWR on 2006-07-27
See the link on [Launchpad]("https://launchpad.net/distros/ubuntu/+source/lighttpd/+bug/46200") (bottom of page) re. this. Adding the exit 0 took care of my problem. I was able to stop the server and then uninstall

---

