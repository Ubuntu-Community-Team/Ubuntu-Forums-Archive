---
title: "How should /etc/hosts read for Samba browsing to work?"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by gregphil on 2008-09-01
With Samba configured and working on a private sub-net of 8 machines 1/2 windows boxes and 1/2 linux distributions, I find it is necessary to set my network "domain" to the peer-to-peer workgroup (= MYGROUP) AND to set smb.conf workgroup = MYGROUP correctly. It also appears to be necessary to edit the /etc/hosts file. (???) But what should the /etc/hosts file look like? My hosts file will only allow browsing when it is set as below (the machine name is 'LIVING-ROOM' and the workgroup is MYGROUP)

127.0.0.1 localhost
127.0.1.1 LIVING-ROOM.MYGROUP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

This means there are at least three separate places where I need to set the "workgroup". Further the network 'domain' setting is getting reset to blank every time I reboot.  Why?  Other Linux distributions (like CentOS 5.2) do not have this problem.

If we hope to be able to compete with Windows someday, the basic stuff like peer-to-peer browsing needs to work AND be simple to setup. :confused:

Thank You.

---

### Post by mrsteveman1 on 2008-09-01
That sounds odd, because hosts is a DNS thing and samba doesn't use DNS, it uses WINS and i believe netbios over TCP broadcasts to find local boxes.

---

### Post by gregphil on 2008-09-01
I am no networking expert, but in a true peer-to-peer network there are no servers (no domain controller, no WINS servers, no servers period).  Peer-to-peer is by far the most common small network setup.

My question is how Ubuntu (and Kubuntu) have chosen to modify the /etc/hosts format to suit the new distributions needs.  under CentOS 5.2 one simply set the 'domain' to the peer-to-peer workgroup and the /etc/hosts file ended up looking like this:

# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1	localhost.localdomain	localhost
::1	localhost6.localdomain6	localhost6
etc

Under ubuntu they seem to have thought up a new scheme.  If it was documented somewhere (anywhere) I could just edit the /etc/hosts file and make it correct.  After two days of effort I finally got peer-to-peer browsing to work with ubuntu / kubuntu, but the 'domain' keeps getting cleared to blank at each reboot.  Then browsing stops working.

Someone must know how to make this work (and stay working)

Thank You.

---

### Post by gregphil on 2008-09-08
Update: authenticated file sharing is broken in ubuntu 8.04.1

The most recent version of ubuntu 8.04.1 switched gnome libraries and broke authenticated file sharing:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

---

