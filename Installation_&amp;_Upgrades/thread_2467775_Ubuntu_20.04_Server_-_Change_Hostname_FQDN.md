---
title: "Ubuntu 20.04 Server - Change Hostname FQDN"
date: 2021-10-07
forum: Installation &amp; Upgrades
---

### Post by penguinpages2 on 2021-10-07
After hours of wasted time and several reinstalls I need some help on how Ubuntu does what should be basics.   


Install host and set name during install to "foo" with static IP. Wireless router which has domain in dhcp of  attnet.local is on same subnet.

I edit hosts file and set

127.0.0.1   localhost 
192.168.1.100  foo.mydomain.local foo

$  hostname 
foo

$ hostname -A
foo.attnet.local

$ cat /etc/resolv.conf
nameserver 127.0.0.53
options edns 0 trust-ad
search mydomain.local

Try to set hostname to clear this up
$ sudo set-hostname foo

$ hostname -a 
foo foo  foo.attnet.local

I am so very confused where it keeps getting this garbage from.  I just want it to think of itself in context where "hostname" returns "foo"  and "hostname -A" returns "foo.mydomain.local

After googling around for hours still not sure where in Ubuntu one can get name resolution to work correctly.

PS: I did eventually break down and install XWindows on one test system and used GUI and ...<sigh> it now works.  But in my case,  GUI (on raspberry pie or other micro linux instances for DevOps) this is not acceptable to use GUI to fix basic name context settings.

---

### Post by ActionParsnip on 2021-10-07
Shouldn't the search domain be your domain not mydomain.local?

---

### Post by MAFoElffen on 2021-10-08
Or rather....
```

sudo hostnamectl server1.example.com

```
Will set the Server's HostName and FQDN in one swipe. Tis the era of systemd.

---

