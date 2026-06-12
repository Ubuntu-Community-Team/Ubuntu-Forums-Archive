---
title: "Cisco VPN client under Ubuntu 6.10"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by ranfr on 2006-12-07
Hi All,

I'm struggling to install cisci VPN client on edgy. I followed the guidelines under:

[http://popey.com/node/62](http://popey.com/node/62)

and created a link to the build:
ln -s /usr/src/kernel-headers-2.4.27-2 /lib/modules/2.6.17-10-386/build

but I still fail ](*,) 

> >/usr/local/src/vpnclient# make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/usr/local/src/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
Makefile:495: /usr/src/linux-headers-2.6.17-10-386/arch/i386/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.17-10-386/arch/i386/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [default] Error 2

Any advise?

---

### Post by GrumpyBob on 2006-12-10
I've been trying to get VPN to work (with Edgy), and had the same issues as you.  I had the same make errors with version 4.7.  I browsed around the web and found version 4.8, which installed straight off.

Now I need to figure out the connection profile to make it work!  Oh how I love a challenge...

Robert

---

### Post by GrumpyBob on 2006-12-10
OK, an update.  I could not make the Cisco client talk to the server.  During the fiddling about, I uninstalled the Cisco client and tried reinstalling it - and it wouldn't.

At this point I gave up with the Cisco client.  I installed vpnc and kvpnc from the repos.

Kvpnc seems pretty easy to use, and works fine in gnome (it sits in the panel).  I found the easiest way to set up vpnc was to start kvpnc, and import the vpn profile from the Cisco client.  I had a vpn profile to hand from installing the WinXP Cisco client (my laptop is dual boot with WinXP).  That made it very easy to set up.  When connecting, I am asked for the RSA passcode from my vpn token (supplied by my work).

To access files on the server, I type smb://server/folder in the address bar of nautilus, and was prompted for username, workgroup and password. 

It all went much more smoothly than with the Cisco client.

Hope this helps,

Robert

---

### Post by anzevi on 2006-12-14
I've just install cisco vpn client on edgy 6.10 without a problem.

Cisco vpn client is vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz 

and uname -a output is here:

Linux mac 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

---

