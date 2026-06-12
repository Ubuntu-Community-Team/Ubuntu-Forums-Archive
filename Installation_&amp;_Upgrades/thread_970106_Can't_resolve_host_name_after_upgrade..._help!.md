---
title: "Can't resolve host name after upgrade... help!"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2008-11-03
Hi,

After upgrading, the system comes up, but problems abound.  Some of the root of these problems seem to stem from being unable to resolve the host name of the system which is parke.ods.org.

For example, if I attempt to restart networking.
After a while I get back a message:
sudo: unable to resolve host parke.ods.org.
This does not seem related at all to the attempt to restart networking, but rather, that the system is stuck attempting to resolve the host name before anything else. 

Before the upgrade I sort of new where to look for this, but not I am a bit clueless.  The System->Preferences->Network tools doesn't list the host name, etc.  And I can't seem to find where this is set.

Please help.

Thanks,
Joel Parke

---

### Post by racmar on 2008-11-03
You can add permanent hostnames to it to /etc/hosts.
```
sudo nano /etc/hosts
```

or ( if you prefer )

```
sudo gedit /etc/hosts
```

you can also read the hostname manual
```
man hostname
```
and you can set it by
```
sudo nano /etc/hostname
```

---

### Post by joel@parke.ods.org on 2008-11-03
Hi,

Thanks for the reply.  I do have a /etc/hostname which is set to parke.ods.org.  The problem is that I don't seem to be able to get out to my dns servers to resolve this.  This feels very weird, since this is the local host.  so something related to the network has gone south in the upgrade.  Although I do have eth1 and eth2 and they look healthy.  

My problem is that I just don't know enough and what was working find in 8.04 is now gone.

Thanks for you help.  Perhaps someone could suggest what else to try.

Thanks,
Joel Parke

---

### Post by racmar on 2008-11-03
try to see if your local dns servers are set in /etc/resolv.conf

---

### Post by joel@parke.ods.org on 2008-11-03
Thanks for the suggestion.

YES - my nameservers are specified in resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220

So there is something more fundamentally hosed.

Thanks.. not sure what else to think about.  
No matter what I try and do, the system complains that host parke.ods.org is not resolved.  But parke.ods.org is setup properly out on [www.ods.org](www.ods.org).

Thanks,
Joel Parke

---

### Post by racmar on 2008-11-03
I just did a nslookup on parke.ods.org and it worked fine for me.  I also use opendns, so that is not your problem.

post what you have in /etc/hosts

---

### Post by joel@parke.ods.org on 2008-11-04
joel@parke:/etc$ cat hosts
127.0.0.1 parke.ods.org.ods.org localhost.localdomain localhost
127.0.1.1 parke.ods.org.ods.org

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.100 laptopjwp

NOW this looks really weird - I can't imagine how parke.ods.org shows up as parke.ods.org.ods.org.

IS this file automatically generated?

Thanks,
Joel Parke

---

### Post by racmar on 2008-11-04
well, that seems odd.  You should probably edit that and remove the extra .ods.org from the first two lines.  I'm not real sure what effect this has on your problem, but my machine does not look like this.  So, make the changes, reboot and let us know if the symptom changed.

also, what do you have for this?
```
hostname -f
```

---

### Post by joel@parke.ods.org on 2008-11-04
Thanks for the help.

I did change this and restarted the network - as opposed to restarting as that is ALSO BROKEN and HANGS with this release.

I have been running with 2 ethernet connections, and have attempted to remove one of them to make things simpler.   But wonderfully, you can't edit the network stuff using the GUI and that seems to be another bug.  Is there anyway to edit the network stuff without doing it manually?  With the changes it is very unclear how to find all the right files.

Overall, I haven't had anything but HUGE problems with this release.  Lets see
1. it broke my network and made it flaky
2. I can't edit the network settings - it says read only.
3. My Twiki pages under apache2 won't run and fail now with a view.pl syntax problem.
4. My imaps connection for mail stopped fuctioning and I had to switch to imap, which seems to work okay - that is when the network is up.
5. I not longer can print to my SAMBA printers on this server.

I hope others have better luck - If anyone has ideas how to resolve some of these issues, I would love to hear about them.

Thanks,
Joel Parke

---

### Post by jimv on 2008-11-04
Things like this is why I do clean installs when new versions come out, rather than using the upgrade 'feature'.

---

### Post by joel@parke.ods.org on 2008-11-04
That's a good idea.... I just wish I didn't have so many hooks into the distribution ... that makes it hard.

But thanks for the thought!

So far I have fixed a number of things, but much more to go....

Thanks again,
Joel Parke

---

