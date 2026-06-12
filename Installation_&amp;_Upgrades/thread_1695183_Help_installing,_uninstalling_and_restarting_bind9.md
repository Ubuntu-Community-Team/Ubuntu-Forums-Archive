---
title: "Help installing, uninstalling and restarting bind9 from source"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by cobeZ on 2011-02-25
Hi
Installing and removing bind with these commands:
sudo apt-get install bind9
sudo apt-get --purge remove bind9
sudo apt-get autoremove
works well,
but i want to install bind from source and i use these commands:
sudo  ./configure -prefix=/usr -sysconfdir=/etc -localstatedir=/var  -disable-threads -without-openssl
sudo make
sudo make install,
and i run into problems.

The first problem is i dont know how to uninstall bind when installed from source, so i install  it with apt and then remove it with apt-get remove.Is there a simpler solution.

The second problem is that when installing from source, restarting with the command
sudo /etc/init.d/bind9 doesn't work.
It says that the command is not found and indeed there is no bind9 file in init.d.

And this started happening 2 days ago, but not before that. Like 2 weeks ago when installing from source with the same command, the restart command work.I dont know what happend(maybe ubuntu did same update), but when i deleted bind, and installed it later it asked me for rndc.conf and .key files, and this didn't happend 2 weeks ago. rndc was not a problem but it showed that samething had changed.

named -v shos bind 9.6

Another problem is when i install bind with apt-get if i have
nameserver 127.0.0.1
in /etc/resolv.conf the resolver looks in my zone files.

When installing from source that same configuration doesnt work.
nslookup times out, and i cant open web sites.

Why do i have this problems when installing bind from source? What am I doing wrong?

---

