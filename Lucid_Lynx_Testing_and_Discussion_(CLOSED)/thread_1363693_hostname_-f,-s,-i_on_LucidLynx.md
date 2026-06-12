---
title: "hostname -f,-s,-i on LucidLynx"
date: 2009-12-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2009-12-24
I am using 64bit LucidLynx.
the hostname suite of commands seem to be behaving differently than
Hardy Heron (and Jaunty).

when I run:
hostname; hostname -f; hostname -s; hostname -i;

I expect to see:
<FQDN>
<FQDN>
<short name>
<the actual IP address>

The only thing I do to a default installation was
edit /etc/hostname and add the domain suffix to the short name.
Such as "machine15.domain.com"
(and reboot)

This is what I get with LucidLynx:
machine15
machine15
machine15
127.0.1.1

Additionally, if I run: `sudo hostname machine15.domain.com`
the command "succeeds", but when I then run `hostname`
i get the short name back.
Seems like the `hostname` command is either not setting
the value in the kernel or is truncating the suffix.

This is my /etc/hosts file and is how all my HardyHeron machines
are set as well.
127.0.0.1 localhost
127.0.1.1 machine15
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by falconindy on 2009-12-24
Your /etc/hosts needs to have a corresponding entry to whatever you're setting the FQDN to.

---

### Post by gmoore777 on 2009-12-28
I logged this as a bug against the LucidLynx release:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501130)

as I think this new behaviour(as compared to HardyHeron)
is not desired.

(the previous reply, by faloconindy, was too vague to do anything with, although I tried various edits in /etc/hosts with no success.
I'm assuming he doesn't have an actual LucidLynx machine and/or was suggesting a solution that would only get me partly there. I clearly do not want to put the actual IP address of the machine in the /etc/hosts file as that defeats the purpose of DHCP/ dynamically allocated IP addresses)

---

### Post by phillw on 2009-12-29
That command gives me, 9.10

> 
phillw@piglet:~$ hostname; hostname -f; hostname -s; hostname -i;
piglet
localhost
localhost
127.0.0.1 127.0.1.1
and on 10.04
> 
phillw@piglet:~$ hostname; hostname -f; hostname -s; hostname -i;
piglet
piglet
piglet
127.0.0.1 127.0.1.1
Apache2 is running on 9.10 & 10.04 (LAMP installation)

Hoping that's of help.

Regards,

Phill.

---

