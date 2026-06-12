---
title: "dpkg: error processing package postfix &amp; bsd-mailx"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by wiovegeex on 2016-08-11
I am running _ubuntu 16.04_ and i just installed **chkrootkit** and **rkhunter** after which i encountered this error every time i try to run an update in the terminal.

    ------------------------------------------------------------   

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up postfix (3.1.0-3) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: pacific-SVE11115EGW..name
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: pacific-SVE11115EGW..name
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

[B]dpkg: error processing package bsd-mailx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 postfix
 bsd-mailx
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]


   ------------------------------------------------------------    

I tried removing both packages using apt-get remove and apt-get clean and autoremove, tried to update and dist-upgrade and i would still get the same error. 

Also tried rebooting the system several times.  

Can anyone please help me? I've been googling this the whole day. Either I cant find the thing I'm looking for or I can't understand what the solution is.

---

### Post by wiovegeex on 2016-08-11
I played with it a bit more.. 

- $ sudo vim /etc/postfix/main.cf 
- removed the extradot in "myhostname = pacific-SVE11115EGW..name"
- $ /etc/init.d/postfix reload (as advised in the terminal)

after which i ran the update && upgrade command and the error was no more :o
/etc/init.d/postfix reload

I hope that was the right thing.. any comments?

---

