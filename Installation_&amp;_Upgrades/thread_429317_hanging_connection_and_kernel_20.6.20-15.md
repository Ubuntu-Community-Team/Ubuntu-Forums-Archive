---
title: "hanging connection and kernel 20.6.20-15"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by nosbod on 2007-05-01
Hi,

i upgraded to feisty from the previous release through the update manager.

Both my wireless card and my ethernet card work........on some sites.
The problem is that I can't connect to any of my work servers. The connection just hangs.
I've tried ssh, http, ftp. The result is the same.

I have tried taking the machine and trying it on a different LAN to the one I am currently on. The result is the same.

Now, if i ssh to another machine on my LAN and from there connect to the work servers i can get a connection. So, it is nothing to do with the LAN setup. It must be feisty. It was and is fine with 20.6.17-11.

Here is what I get when I run ssh -v

OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 138.37.x.x [138.37.x.x] port 22
debug1: Connection established.
debug1: identity file /home/bla/.ssh/identity type -1
debug1: identity file /home/bla/.ssh/id_rsa type -1
debug1: identity file /home/bla/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version 3.2.0 SSH Secure Shell (non-commercial)
debug1: no match: 3.2.0 SSH Secure Shell (non-commercial)
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: SSH2_MSG_KEXINIT sent

And then it just hangs.
Anybody any ideas?
(I've commented out the GSSAPI lines in the ssh_config.)

Any help appreciated, this has me totally stumped and preventing me working from home!!
I'm going to downgrade if I can't get anywhere with this.

cheers

---

### Post by Giblet5 on 2007-11-01
I can confirm this on Feisty and Gutsy.

It will hang at "debug1: SSH2_MSG_KEXINIT sent" when connecting to a work server (RH with 3.7.1p2 sshd). SSH from Gutsy or Feisty to Dapper works fine.

I too disabled the GSSAPIAuthentication. No joy.

I set my NAT router, and my Gutsy NIC to MTU: 576. This changes the point at which it (appears to) hang. I'm convinced this is unrelated, since a dapper box, with the same MTU (1500), going through the same router, works fine (no matter what the NIC or router are set to).

Dapper uses ssh v4.3p2.

I grabbed and built openssh 4.3p2 for Gutsy. Same thing.

It's silly that I have to maintain a Dapper machine so that SSH will work, but that's where it stands.

I will name my next child whatever you demand if you can point me at a fix.

---

