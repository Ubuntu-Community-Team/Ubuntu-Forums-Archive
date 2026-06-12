---
title: "Upgrade failed crash: I am really angry now."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2006-10-27
OK, after the upgrade from Dapper to Edgy was running all night and half a day I got a crash message: 

"The upgrade aborts now. Your system could be in an unusable state. A recovery wa
s run (dpkg --configure -a)"

I can still use my brower but "Your system could be in an unusable state" does not sound encouraging, so I'd rather not try and re-boot for now.

What can I do now?? 

In main.log the last entry is:
2006-10-27 15:17:55,530 ERROR SystemError from cache.commit(): installArchives() failed
apt.log has a number of messages about broken dependencies.
term.log has this:
Errors were encountered while processing:
 lighttpd
Traceback (most recent call last):
  File "/usr/lib/python2.4/logging/__init__.py", line 740, in emit
    self.flush()
  File "/usr/lib/python2.4/logging/__init__.py", line 718, in flush
    self.stream.flush()
IOError: [Errno 9] Bad file descriptor
edgy: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
Setting up lighttpd (1.4.13~r1370-1ubuntu1) ...
 * Starting web server lighttpd
 * Starting web server lighttpd 2006-10-27 15:17:57: (network.c.300) can't bind to port:  80 Address already in use
                                                                         [
                                                                         [fail]
invoke-rc.d: initscript lighttpd, action "start" failed.
dpkg: error processing lighttpd (--configure):
 subprocess post-installation script returned error exit status 1

Of course, before the upgrade I had disabled lighthttp and enabled apache which is running on port 80.

What state is my computer in now? Is it safe to reboot? What to do?



What now?

---

### Post by johann_p on 2006-10-27
It seems that the update process wanted to install lighttpd and start the server on port 80, but I had already apache installed and started. I manually removed lighttpd and re-ran update-manager and it completed somehow.

Things seems to work, but when I look at the update manager i see a list of updates that are greyed out and do not allow to be checked. What does this mean????

---

### Post by bulldog on 2006-10-27
In most case that means there are updates but they don't get installed because of dependency errors.

You have probably programs installed which not came from the Ubuntu repo's.

---

### Post by johann_p on 2006-10-27
> **bulldog said:**
> In most case that means there are updates but they don't get installed because of dependency errors.

You have probably programs installed which not came from the Ubuntu repo's.

I think you are right.  I found some info on the internet and could overwrite this with "adept dist-upgrade". So it seems this was unrelated with the preceding update manager crash.

---

### Post by Paul Dufresne on 2006-10-27
* Starting web server lighttpd 2006-10-27 15:17:57: (network.c.300) can't bind to port: 80 Address already in use

I am not an expert at all, but reading previous, I come to the conclusion
that it tried to start lighttpd, but found apache already running
on port 80.
Guess you should have let lighttpd running before upgrading.
It would have stopped last version before upgrading lighttpd, and then
would have it restarted just after upgrading the packet.

Not sure what to think of previous messages however.

---

