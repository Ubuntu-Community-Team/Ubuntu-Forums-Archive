---
title: "Disabling ipv6 on kernel 2.6.28-4?"
date: 2008-12-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by marmuta on 2008-12-30
Is there still a way to disable ipv6? Looks like the modprobe.d based solutions stopped working because the latest kernel has the module build in.
Anything I can do to make it go away?

---

### Post by ronacc on 2008-12-30
that explains why my access time went south with the -4 kernel

---

### Post by rfruth on 2008-12-30
here is how I did it and it worked like a charm (on my Debian Lenny box)

> As root:


    * vi /etc/modprobe.d/blacklist
    * Go to the end of this blacklist file and add "blacklist ipv6" without the quotation marks
    * Save and exit vi
    * vi /etc/modprobe.d/00local
    * Add "alias net-pf-10 off" on one line and "alias ipv6 off" on another line to this file, which may be new
    * Save and exit vi


Reboot and you should be good to go. Oh and don't use quotations in the "00local" file either

---

### Post by marmuta on 2008-12-30
Yep, that and maybe firefox hammering dns. Mine keeps sending dns queries for every single image. Seems to have forgotten how to cache ip addresses.

I've found these kernel parameters and put them in /etc/sysctl.d/60-meins.conf, but it didn't seem to make much of a difference yet.

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

---

### Post by ronacc on 2008-12-30
I have been doing that for a long time , it no longer seems to work with the 2.6.28-4 kernel .

EDIT to add info . not just FF (all versions) but Opera (9.62 and 10b) also epiphany dillo  and every other one I tried .

---

### Post by marmuta on 2008-12-30
@rfruth: Thank you, but this doesn't seem to work anymore because there is no external module to blacklist. Ipv6 is build into the kernel.

---

### Post by ayates on 2008-12-30
Yes, they have changed a lot of modules to built in. I gather the reason is for boot speedup. I boot charted 3 vs. 4 and it saved a total of 2 seconds. Here is a list of the now builtin modules:

---

### Post by marmuta on 2008-12-30
> **ronacc said:**
> EDIT to add info . not just FF (all versions) but Opera (9.62 and 10b) also epiphany dillo  and every other one I tried .

Weird, is there a bug report somewhere? I couldn't find one.

---

### Post by ronacc on 2008-12-30
If ipv6 is built into the kernel its not a bug its a feature:lolflag: I dind't make one I was in the process of troubleshooting it when I destroyed my jaunty install and todays dailys wouldn't install so Im jackalopeless right now:)

---

### Post by DougieFresh4U on 2008-12-30
> **ronacc said:**
>   I destroyed my jaunty and todays dailys wouldn't install so Im jackalopeless right now:)

Sorry to hear that,I'm sure you'll be up and Jackaloping in no time

---

### Post by marmuta on 2008-12-30
> **ronacc said:**
> If ipv6 is built into the kernel its not a bug its a feature:lolflag:

:) I meant the broken FF dns caching, which is unrelated to ipv6 and totally off-topic anyway. I'll see if I can figure out a package to file it under.

ipv6 may as well morph back to a module again if there is no other option to turn it off. You can't have the jackalope lagging in the tubes for a few tenths of a second gain in boot time.

hope you get your jackalope revived soon.

---

### Post by gnomeuser on 2008-12-31
Disabling a feature like ipv6 is just pushing the issues ahead of us. Eventually we will need to fix these little bugs because we are running out of ip space in v4. If Ubuntu wants to be a competitor in the future ipv6 readiness is important.

I would kindly request that bugs be filed instead, yes it sucks hard that you (and the rest of us) have issues, but to solve them this is the right approach. This is an early development release of Ubuntu afterall, issues should be expected.

---

### Post by ronacc on 2008-12-31
I agree that we need to support IPV6 ,but the "module method " atleast gave those of us who needed to disable it the ability to do so when we had to . I am not sure whether it is my router or my isp but having ipv6 enabled causes me to have very slow flaky access times.If it is my router it's fixable , if it is my isp I'm stuck until they come into compliance .

---

### Post by keep-on-smiling on 2008-12-31
Hi

Just thought I would add my 2 cents' worth here - I run a Shiro DSL805E router here in South Africa where connectivity is um... fun! the max my line will give me is 39/40 kb (384 line - entry-level). 

This has been fine with Jaunty (running the CD from Christmas Day - my pressie to myself :) ).

Cheers

---

### Post by marmuta on 2009-01-03
Happy new year! Just a follow up to fill some gaps. 

Thank you ronacc for filing bug [#313218]("https://bugs.launchpad.net/bugs/313218") for the return of the ipv6 module.

1) I've been trying to find another way to turn off ipv6, but to no avail. For what it's worth, this script removes inet6 addresses from all interfaces.
It goes in /etc/network/if-up.d/00-disable-ipv6.
```
#!/bin/sh
addr=$( ifconfig $IFACE | grep -o "[[:xdigit:]:]*/[[:digit:]]*" )
[ ${#addr} ] && ip -6 addr del $addr dev $IFACE 

```
You probably don't want it though. It doesn't stop name resolution from doing AAAA queries and
some processes still bind to the unspecified ipv6 address ::.
This is problematic for at least vino [bug #228370]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug #228370") and gobby [bug #313393]("https://bugs.launchpad.net/ubuntu/+source/gobby/+bug/313393"), they become inaccessible for ip4. Breaks my VPN.

2) The kernel variables "disable_ipv6" from a few posts ago actually do have an effect in that they block all communication over ipv6 addresses.
```
sudo sysctl net.ipv6.conf.lo.disable_ipv6=0
ping6   ::1     # works
sudo sysctl net.ipv6.conf.lo.disable_ipv6=1
ping6   ::1     # blocks indefinitely
```
but again, ip6 addresses stay valid, so apps and deamons still bind to them and ip6 name resolution (AAAA records) via ip4 is still occuring.

3) The off-topic issue with firefox hammering dns had actually three reasons. 
Me using a local web-proxy, firefox 3.1 doing the new [dns-prefeching]("http://bitsup.blogspot.com/2008/11/dns-prefetching-for-firefox.html") by default and last but not least more dns traffic with ipv6 enabled.
There were no bugs, just features ;). 

Still needed some relief and installed dnsmasq which made it all usable again.
Before, visiting [en.wikipedia.org]("http://en.wikipedia.org/wiki/Main_Page") created 119 packets of dns traffic. With dnsmasq it's down to 9.

---

### Post by luca_linux on 2009-01-03
In Firefox's about:config there is the "network.dns.disableIPv6" option. Maybe it could help speeding up the network access as long as Firefox is concerned.

---

### Post by marmuta on 2009-01-03
Thanks, I forgot about that one in the 3.1 profile. Works in epiphany-gecko too.
Only 5 dns packets for wikipedia now.

---

### Post by marmuta on 2009-01-04
One more update to rectify things.

My point from above, where I claimed vino/gobby would loose ip4-connectivity is incorrect. 
Thanks [Armin]("https://bugs.launchpad.net/ubuntu/+source/gobby/+bug/313393") for the nudge.

It does work, magically so, by way of an IPv6 transitioning feature called [IPv4 mapped address]("http://en.wikipedia.org/wiki/IPv4_mapped_address").
This is turned on with "sysctl net.ipv6.bindv6only=0" which is the default for Jaunty.
Basically the IPv6 port transparently allows IPv4 connections too.
That's why netstat/lsof don't show an IPv4 port whereas nmap does.
```
$ netstat -taupn|grep gobby 
tcp6 0 0 :::6522 :::* LISTEN 21125/gobby     
$ nmap localhost -p6522 | grep open
6522/tcp open  unknown

```

> **gnomeuser said:**
> Disabling a feature like ipv6 is just pushing the issues ahead of us. Eventually we will need to fix these little bugs because we are running out of ip space in v4.

I guess I'm running out of complaints. I hope the others get their speed issues resolved though.

---

