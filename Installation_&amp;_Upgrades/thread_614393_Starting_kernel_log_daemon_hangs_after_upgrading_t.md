---
title: "Starting kernel log daemon hangs after upgrading to 7.10"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by vohinh on 2007-11-15
Hi all, I'm new to Ubuntu and Linux too, please help me.

I installed Ubuntu from the live cd before and yesterday I saw the report to upgrade to 7.10.
The upgrade process happened normally, I decided to keep all old configuration files because I don't want to re-config all those packages.

But after the upgrade process finish and I choose restart now, the running progress bar on the start screen suddenly stop for a while and then it change to text screen and my pc hangs at the line "Starting kernel log daemon", there isn't an [ok] also, I waited for 10 minutes but it still hangs there, the keyboard still work normally, I can restart the pc by pressing Ctrl + alt + del.

I totally lost here, please help me, I've installed many things and there're lot of my works in the hard disk.

---

### Post by tylerjoh on 2007-11-16
Same symptom in my case

Workaround is to remove ldap from /etc/nsswtich.conf. This at least lets the server boot normally. Not too useful in my case because none of my ldap users can log in.

---

### Post by crazybeard on 2007-11-28
I too am using 7.10 and after successfully configuring my client laptop for ldap, was horrified to run into this problem.   Commenting out the ldap stuff in my nsswitch.conf file fixed it.   The frustrating part is that this has been a problem for over a year and yet it still shows up.

I think the problem is mainly due to the fact that configuring ldap for linux is simply not trivial, although there are a couple of distros that have simplified the process quite effectively.

Here is a link to a thread that seems to have hit on some solutions, although I haven't tried them yet:

[https://launchpad.net/ubuntu/+source/libnss-ldap/+bug/51315](https://launchpad.net/ubuntu/+source/libnss-ldap/+bug/51315)


cbm

---

### Post by iiibill on 2008-01-09
Where is the ldap server running?  If it is on the local system that might be the problem.  I noticed that I could not get any init.d scripts past the kernel log startup to run after updating to the most recent version of pam/nss ldap.  It looks like the startup process is waiting for the ldap service.  I have multiple ldap servers running so I was able to work around it but setting the hosts value in /etc/ldap.conf to:

hosts 127.0.0.1 205.154.12.12

Where the second IP is the address of one of the replicas.

Bill

---

### Post by sean on 2008-01-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/libnss-ldap/+bug/155947](https://bugs.launchpad.net/ubuntu/+source/libnss-ldap/+bug/155947) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is the bug:

[https://bugs.launchpad.net/ubuntu/+source/libnss-ldap/+bug/155947](https://bugs.launchpad.net/ubuntu/+source/libnss-ldap/+bug/155947)

I can confirm this in Gutsy when configured as an LDAP client.  I would say this is fairly crippling if you ask me.  I am not sure how Canonical can claim Ubuntu is "Enterprise Ready" with rather egregious bugs like this one.

Sean

---

### Post by thk on 2008-01-16
Ya, that's a show stopper. I'm just upgrading desktop clients and am hitting this bug. The odd thing is that some are working while others are not and I cannot figure out why. I remember the LDAP init problem from earlier releases (popped up with the switch to upstart), but if you waited long enough (10 minutes or so) it would timeout and continue. Now they just freeze. I know there are big plans out there to improve all of this. It would be nice however if bugs in the existing setup got fixed along the way!

---

