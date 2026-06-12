---
title: "initializing kernel log failed after 686 kernel"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2005-10-26
I just installed the kernel image 686 tru apt-get and while it was booting, it said (on the splash screen that says "ubuntu") that initializing kernel log failed. Why could this be? And, is it important? should I just ignore it, or try to fix it? thanks.

---

### Post by Xian on 2005-10-26
Does it do this on subsequent boots?

---

### Post by towsonu2003 on 2005-10-26
[QUOTE=Xian]Does it do this on subsequent boots?[/QUOTE]

I will have to get back to you a little bit later (tomorow). It is very hard for me to connect to internet as this slmodem (precompiled, using wvdial to dial up) keeps giving errors. 

And (it's gonna be like advertising but) here is my posts on that slmodem problem:

[http://ubuntuforums.org/showthread.php?t=73049](http://ubuntuforums.org/showthread.php?t=73049)

[http://ubuntuforums.org/showthread.php?t=76065](http://ubuntuforums.org/showthread.php?t=76065)

---

### Post by towsonu2003 on 2005-10-27
[QUOTE=Xian]Does it do this on subsequent boots?[/QUOTE]

sorry about the delay. Yes it does do it (fail to initialize that is) on every boot (4 boots so far). :confused:

anyone? i'm not used to stuff failing in boot (except that time thing) with ubuntu so i'm a little panicky...

---

### Post by towsonu2003 on 2005-10-29
any ideas from any one? I still have this problem...

---

### Post by Kyral on 2005-10-29
If its the bootlog daemon, don't worry its always gonna fail, but its still working ;P

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=Kyral]If its the bootlog daemon, don't worry its always gonna fail, but its still working ;P[/QUOTE]

could you clarify that a little bit more for me? (or a pointer?)

Also, how to check whether this kernel log (don't know which file it corresponds to) is running or not?

I'm not sure whether this kernel log is the same as bootlog deamon. The only thing I know is it says "Initializing kernel log ................ Failed" in the boot screen (under that big ubuntu picture - you know, where those messages go up as it does the boot procedure). 

Thanks for the reply.

[Edit] Too many words due to not enough english knowledge :)

---

### Post by Kyral on 2005-10-29
Check out the /var/log directory to see if its generating logs.

Anyway its not a really critical thing, the boot log

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=Kyral]Check out the /var/log directory to see if its generating logs.

Anyway its not a really critical thing, the boot log[/QUOTE]

/var/log has logs generated in it, i usually use the gui system log to look at them.

keeping in mind that i boot this laptop 3 times a day on the average;
using nautilus to look in /var/log:
there is no log named boot or bootlog or *boot* (* as wildcard)
date modified for kern.log is 5 days ago; for kern.log.0 is 8 days ago, kern.log.gz is 12 days ago
there is also a file called kernel (with strict root permissions) that has 0 bytes in it... 

also these are the files that were modified today (which means they are working after my kernel change):
evms-engine.1.log
dpkg.log
syslog.0
Xorg.0.log.old
evms-engine.log
dmesg
Xorg.0.log
lastlog
daemon.log
user.log
acpid (strict root permissions)
auth.log
loginlog
messages
syslog
wtmp

---

### Post by towsonu2003 on 2005-10-29
it seems "initializing kernel log" corresponds to sysklogd, which writes to multiple log files in /var/log . 

it seems i have a problem with kern.log, which appears to be empty! 

i have absolutely no idea how to diagnose and fix this ... please help...

---

### Post by towsonu2003 on 2005-11-01
bump

---

### Post by towsonu2003 on 2005-11-01
pls go to this post, which is much more brief and complete:

[http://www.ubuntuforums.org/showthread.php?p=461188#post461188](http://www.ubuntuforums.org/showthread.php?p=461188#post461188)

thanks

sorry for the double post, I thought the other one would be much better. 

please delete this if you should.

---

