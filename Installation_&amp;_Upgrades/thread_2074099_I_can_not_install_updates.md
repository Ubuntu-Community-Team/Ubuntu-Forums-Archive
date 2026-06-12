---
title: "I can not install updates??"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by LionsFootball on 2012-10-20
Hello, whenever I try to install updates it tells me to do the following command "Terminal: apt-get install -f". 

I put it in the terminal and I get this:

"E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

What do I put in next? 

Thank you!

---

### Post by drmrgd on 2012-10-20
As that's a system level command, you need to run it with sudo.  Try:

```
sudo apt-get install -f
```

---

### Post by LionsFootball on 2012-10-21
Okay, here is what i got this time.

-

bigbertha@ubuntu:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bigbertha@ubuntu:~$ sudo apt-get install -f
[sudo] password for bigbertha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmtp-dev
The following packages will be upgraded:
  libmtp-dev
1 upgraded, 0 newly installed, 0 to remove and 471 not upgraded.
1 not fully installed or removed.
Need to get 0 B/10.6 kB of archives.
After this operation, 395 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libmtp-dev:
 libmtp-dev depends on libmtp8 (= 1.0.2-1ubuntu1); however:
  Package libmtp8 is not installed.
dpkg: error processing libmtp-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libmtp-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
bigbertha@ubuntu:~$ 

-

---

### Post by snowpine on 2012-10-21
The "-f" flag means "fix broken" so you might want to back up a step and figure out *why* you have broken packages. In my experience this is usually a result of mixing unsupported 3rd-party repos into your software sources; take a look in your /etc/apt/sources.list for anything you might have added that doesn't have an "ubuntu.com" domain name, then try again. :)

---

### Post by Old_Grey_Wolf on 2012-10-21
[s]To remove the lock file enter this command ```
sudo rm /var/lib/apt/lists/lock
```[/s]

After rereading the post I see that wasn't the problem you were having.

---

