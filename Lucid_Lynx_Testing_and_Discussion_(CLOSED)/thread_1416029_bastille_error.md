---
title: "bastille error"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Saghaulor on 2010-02-25
Hello All!

I'm setting up a 10.04 i386 server to use as a web app testbed. I figured I'd harden it as I've read online that hardening has a significant security bonus.

I figure I'd test Lucid Lynx as I'd like to give back what I can, as Ubuntu and its community have been so good to me.

I installed bastille since I'm familiar with it. 

After answering all of the questions, I noticed an error message in the console.

The message was as follows:

> ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 5.0.


I do not know what this means. Did bastille write a configuration file? Should I go about hardening it in another way? Please advise.

---

### Post by cariboo on 2010-02-25
I don't know If I'd want to use Bastille any more, as it hasn't been updated since early 2008, it looks like development has stopped. That may be why you're getting the error message.

---

### Post by Saghaulor on 2010-02-25
> **cariboo907 said:**
> I don't know If I'd want to use Bastille any more, as it has been updated since early 2008, it looks like development has stopped. That may be why you're getting the error message.

Ah, good point. Any suggestions on a different hardening product?

---

### Post by nickmcg on 2010-02-26
I'd also be interested in an alternative - the installation in karmic failed with```
Unpacking bastille (from .../bastille_1%3a3.0.9-12_all.deb) ...
Selecting previously deselected package psad.
Unpacking psad (from .../archives/psad_2.1.5-1_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up bastille (1:3.0.9-12) ...
WARNING: Bastille-firewall is not configured yet
Please create /etc/Bastille/bastille-firewall.cfg to enable it.
(HINT: use InteractiveBastille)

Setting up psad (2.1.5-1) ...
Starting Port Scan Attack Detector: psad [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 9566.
 * Unable to start the daemon.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error processing psad (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Attempting to run InteractiveBastille gave the same error as above.

Nick

---

### Post by Saghaulor on 2010-02-26
> **nickmcg said:**
> I'd also be interested in an alternative - the installation in karmic failed with```
Unpacking bastille (from .../bastille_1%3a3.0.9-12_all.deb) ...
Selecting previously deselected package psad.
Unpacking psad (from .../archives/psad_2.1.5-1_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up bastille (1:3.0.9-12) ...
WARNING: Bastille-firewall is not configured yet
Please create /etc/Bastille/bastille-firewall.cfg to enable it.
(HINT: use InteractiveBastille)

Setting up psad (2.1.5-1) ...
Starting Port Scan Attack Detector: psad [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 9566.
 * Unable to start the daemon.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error processing psad (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Attempting to run InteractiveBastille gave the same error as above.

Nick

It looks like theres at least one option in the repo's.
[http://packages.ubuntu.com/lucid/harden]("http://packages.ubuntu.com/lucid/harden")

---

### Post by cariboo on 2010-02-26
Check bodhi.zazen's security guides [here]("http://ubuntuforums.org/showthread.php?t=1046738").

---

### Post by Saghaulor on 2010-02-28
> **cariboo907 said:**
> Check bodhi.zazen's security guides [here]("http://ubuntuforums.org/showthread.php?t=1046738").

Funny thing, I was just thinking to myself I should check the forums to see what bodhi.zazen has to say. And then you posted a link to his thread on security.

Thanks.

---

