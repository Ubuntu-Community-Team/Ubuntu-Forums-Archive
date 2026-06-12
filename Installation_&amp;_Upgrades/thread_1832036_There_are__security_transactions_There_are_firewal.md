---
title: "There are  security transactions? There are firewall, antivirus, antispam for Ubuntu?"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2011-08-24
hello,
apology again for my English...
There are  security transactions? There are firewall, antivirus, antispam for Ubuntu linux?
how do I install the "Google Talk"? how can I "Chat" with my gmail account?
I wait for your answer...
thanks a lot...

---

### Post by haqking on 2011-08-24
> **spi_ said:**
> hello,
apology again for my English...
There are  security transactions? There are firewall, antivirus, antispam for Ubuntu linux?
how do I install the "Google Talk"? how can I "Chat" with my gmail account?
I wait for your answer...
thanks a lot...


Linux does not suffer from Viruses Like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords etc.

Common sense, dont tell your system you want it to do something unless you are sure etc.

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox etc.

Also look at apparmor for profiling your applications and there privelege

See below staring with Bodhi.Zazen overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

then here for AV information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

As for firewalls, no ports are open by default and you should be protected by your router firewall, if you wish to run services on your box then you can use IPTables/netfilter which is the firewall built into the kernel and you can manage it from command line or through UFW or graphically with GUFW.

see **man iptables** or** man ufw** from terminal for more information.

As for googletalk there are a few clients.

I personally use pidgin for googletalk, msn and skype and ICQ.

enjoy

---

