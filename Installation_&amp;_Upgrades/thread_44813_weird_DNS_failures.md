---
title: "weird DNS failures"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by rossjesse on 2005-06-27
Hello - I just installed Hoary Hedgehog 5.04 on an IBM ThinkPad T42.  It has booted up fine, and I have two network connections - one wired and one wireless.   Each has gotten an IP address, and the right nameservers are showing up in my resolv.conf.

However, I can't get programs to do DNS lookups - Firefox, Evolution (IMAP) and the terminal services client all fail with some variant of "temporary failure in name resolution".

The truly bizarre thing about this is that I can resolve names no problem, using 'host' or 'nslookup'.  Queries using these tools return answers basically right away.  So why can't the other programs read the DNS?

Here is a shell session as an example of the kind of problem I am running into - I'm trying to hit a webserver here:

$ host cyber.law.harvard.edu
cyber.law.harvard.edu has address 140.247.216.113
$ telnet cyber.law.harvard.edu 80
telnet: could not resolve cyber.law.harvard.edu/80: Temporary failure in name resolution
$ telnet 140.247.216.113 80
Trying 140.247.216.113...
Connected to 140.247.216.113.


Does anyone have any ideas?

Thanks very much,
jesse

---

### Post by Arthemys on 2005-06-27
Common problem that pretty much no one can really put a finger on. My fiance and I are blaming it on the built-in IPv6 support that's not really needed by anyone that causes these problems.

One thing I've noted that helps a lot is if you're using GNOME, (This is what I do) you go into your network settings and deactivate the wireless or wired connection, whichever you're currently not using and make sure that the current connection is set as the default gateway. In addition I use DNS servers provided by OpenNIC... They seem to work the best for me.

---

### Post by rossjesse on 2005-06-27
[QUOTE=Arthemys]Common problem that pretty much no one can really put a finger on. My fiance and I are blaming it on the built-in IPv6 support that's not really needed by anyone that causes these problems.

One thing I've noted that helps a lot is if you're using GNOME, (This is what I do) you go into your network settings and deactivate the wireless or wired connection, whichever you're currently not using and make sure that the current connection is set as the default gateway. In addition I use DNS servers provided by OpenNIC... They seem to work the best for me.[/QUOTE]
 Well, that fixed it!  I just disabled the wired connection, and everything is working fine now.  Likewise, if I disable the wireless connection and use the wired one, it works fine that way too.

I still don't understand *why* this works, but I'm happy for now!  :)

Thanks very much, Arthemys.

---

### Post by Arthemys on 2005-06-27
No problem! I don't really get it either, at this stage in my linux life, I'm just a "user" perse.

---

