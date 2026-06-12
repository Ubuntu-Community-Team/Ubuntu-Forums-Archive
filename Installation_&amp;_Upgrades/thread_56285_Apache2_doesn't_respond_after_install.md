---
title: "Apache2 doesn't respond after install"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by potterzot on 2005-08-12
Hi, I can't seem to find info about this problem:

installed apache2, php4, and mysql with apt-get.  Problem is, I can't get a response from [http://localhost](http://localhost)  also, if I ping localhost I get nothing back...actually, looks like nmap also gives that the host is down or blocking ports.  So I am guessing it has something to do with ports not being opened.  Is that an xinetd thing?  Help is appreciated.

Thanks

---

### Post by heimo on 2005-08-12
Is it running?
 ```
ps aux | grep apache
``` shows couple apache2 processes?

Does it start?
 ```
sudo /etc/init.d/apache2 start

``` says ok?

Does it stop?
  ```
sudo /etc/init.d/apache2 stop

``` says ok?

Is configuration files syntax ok?
 ```
apachectl configtest

```  says ok?

EDIT:
Do you run firewall?

Check 80 port on local machine:
 ```
nmap -p80 localhost

``` says it's open?

---

### Post by potterzot on 2005-08-12
Thanks for the response.

Yes to everything.  Except the nmap stuff.  nmap -P0 localhost shows all ports filtered.  I didn't set up a firewall, but I am wondering if one is on by default and you have to turn it off.  iptables? (or is that openbsd?).  Apache is running, can be started, stopped, etc...

There must be some kind of security program blocking ports.  Does Ubuntu start with all ports filtered?

I'll check around on that.

Thanks again

---

### Post by potterzot on 2005-08-14
In case anyone else is as ignorant as me, my problem was that apache and sshd were running over ipv6 instead of ipv4.  if you add:

alias net-pf-10 off

to the /etc/modutils/aliases file, and restart, you are all set.

Thanks for you help

---

