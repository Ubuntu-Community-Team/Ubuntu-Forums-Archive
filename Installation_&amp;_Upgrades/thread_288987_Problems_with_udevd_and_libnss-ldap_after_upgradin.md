---
title: "Problems with udevd and libnss-ldap after upgrading from Dapper to Edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by sepan77 on 2006-10-30
I configured my system with ldap authentication. After upgrading to Edgy Eft, I've the following error messages at boot time:

udevd: nss_ldap: Can't contact server https://server.intern

It retries to contact my ldap server (I don't know why it has to, since udev should only populate my /dev) for a few times and every time it fails, it is waiting for 4, 8, 16, 32, 64 seconds and giving up after that (so my boot-time increases by 124 seconds).

How can I fix that?

My /etc/libnss-ldap.conf reads:
----------
host server.intern
base ou=People,dc=xxx,dc=at
uri ldaps://server.intern/   
ldap_version 3

nss_base_passwd ou=People,dc=xxx,dc=at
nss_base_group  ou=Group,dc=xxx,dc=at
----------

---

### Post by dchenbecker on 2006-10-30
> **sepan77 said:**
> I configured my system with ldap authentication. After upgrading to Edgy Eft, I've the following error messages at boot time:

udevd: nss_ldap: Can't contact server [https://server.intern](https://server.intern)

It retries to contact my ldap server (I don't know why it has to, since udev should only populate my /dev) for a few times and every time it fails, it is waiting for 4, 8, 16, 32, 64 seconds and giving up after that (so my boot-time increases by 124 seconds).

How can I fix that?
----------

I had the exact same problem. I haven't had time to research the "correct" solution but in my case I found a quick hack. What's happening is that somehow udevd has a dependency on libnss_ldap (possibly looking up uids in the password file), but it tries to come up before the NIC is enabled and online. As a quick workaround I merely dropped in a quick script called S09quicknet into /etc/rcS.d :

```

#/bin/sh

modprobe e1000 # load the nic module

dhclient3      # fire up DHCP

```

You can modify as appropriate to at least get a system that will boot. Make sure that the file is executable or it won't get run during init. Maybe this weekend I'll have more time to investigate the issue.

Derek

---

### Post by sepan77 on 2006-10-30
Thank you, I had the same idea by reordering the startup-scripts in /etc/rcS.d, but this turned out to be a very bad idea.
I'll try your approach for a quick hack. 
Thank you.

---

### Post by dchenbecker on 2006-10-30
Yeah, I'd be careful about reordering. Just bringing up the NIC for the moment should at least get things working, and when/if a fix is determined it's simple to undo the change.

Derek

---

### Post by puelocesar on 2006-10-31
Can anyone figure any other solutions? This hack is not working for me, since I don't have a dhcp server and I don't know how to configure my network with command line ..

"ifconfig eth1 'ip' netmask 'mask' up" didn't worked

---

### Post by dchenbecker on 2006-10-31
That ifconfig command should have worked. Is your LDAP server on another subnet? If it is then you'll have to also add a default route. You should at least see some console messages about the NIC coming up when that command runs.

Derek

---

### Post by nocturn on 2006-10-31
Me too...

I have a solution that worked on Dapper, but it'll have to be modified for upstart in Edgy.

I basicly have an init script that copies over nsswitch.conf.
On bootup, it puts the ldap enabled one after network startup, on shutdown it copies the distro default back.  

This makes udev and hal work again...

---

### Post by simidau on 2006-11-05
Don't know if there are any repercussions however another "fix" for this problem seems to be setting 

bind_policy soft

in /etc/libnss-ldap.conf there may be another file you have to change it in also however i can't remember the name of it.

Going to reboot now and see if just that file needs to be changed. - Worked.

The theory here is when the machine fails to connect to the LDAP server it fails instantly and continues on. Once networking comes the LDAP server will be visible, I can imagine this fix would cause problems if your LDAP server was not on a LAN and sometimes you have issues connecting to it.

---

### Post by nocturn on 2006-11-06
> **simidau said:**
> Don't know if there are any repercussions however another "fix" for this problem seems to be setting 

bind_policy soft

in /etc/libnss-ldap.conf there may be another file you have to change it in also however i can't remember the name of it.

Going to reboot now and see if just that file needs to be changed. - Worked.

The theory here is when the machine fails to connect to the LDAP server it fails instantly and continues on. Once networking comes the LDAP server will be visible, I can imagine this fix would cause problems if your LDAP server was not on a LAN and sometimes you have issues connecting to it.

I helps as that the retries do not hang the system for minutes on end.  But still, udev fails to start here.

---

### Post by dchenbecker on 2006-11-06
I don't know if I'm reading everything correctly, but it appears that's its a circular dependency. Udev is responsible for bringing up the network hardware, but it also implicitly needs nss to check permissions and get user/group info. I don't know enough about all of the underlying mechanisms to think of any fix other than the hack I put together.

Derek

---

### Post by nocturn on 2006-11-06
> **dchenbecker said:**
> I don't know if I'm reading everything correctly, but it appears that's its a circular dependency. Udev is responsible for bringing up the network hardware, but it also implicitly needs nss to check permissions and get user/group info. I don't know enough about all of the underlying mechanisms to think of any fix other than the hack I put together.

Derek

Yes, it's a circular dependency.
The problem is that udev has all the info it needs in the local files.  It should not fail because libnss-ldap fails.

I have a hack working on Dapper, but it needs to be modified for Edgy (with upstart).

I copy the ldap enabled nsswitch.conf in place before starting nscd, I copy the default one back after shutting down nscd.
This should work on Edgy too.

---

### Post by wensveen on 2006-11-14
There is a bug reported on launchpad: [https://launchpad.net/distros/ubuntu/+source/libnss-ldap/+bug/51315](https://launchpad.net/distros/ubuntu/+source/libnss-ldap/+bug/51315)

A .deb package is available from Lionel Porcheron. Haven't tested it though, but there seems to be progress in any case.

---

### Post by Ralf Becker on 2006-11-14
I've posted this to [https://launchpad.net/distros/ubuntu/+source/libnss-ldap/+bug/51315](https://launchpad.net/distros/ubuntu/+source/libnss-ldap/+bug/51315). 

-------------------8<------------------------------------------
I've have had the same problem, found the reason and solved it.

The problem is caused by the usage of the non existing group 'nvram' in /etc/udev//rules.d/40-permissions.rules:
...
KERNEL=="nvram", GROUP="nvram"
...

When udev starts, is looks up 'nvram'. While 'nvram' could not be found in /etc/group NSS tries to connect the ldap server. As result the boot sequence stops.

To fix this problem is very easy: Add the local group 'nvram' to /etc/groups

After that booting with nss_ldap and bind_policy hard works without any problem.
---------------------->8----------------------------------------

---

