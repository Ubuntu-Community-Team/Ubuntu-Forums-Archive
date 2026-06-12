---
title: "SSH client slow after upgrade"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by minkcar on 2011-10-20
I just upgraded from Natty to Oneiric, and things went really smoothly except that now when I ssh to a remote server it takes about 10 seconds to prompt for the password.  I regularly remote to 4 servers (RedHat and HP-UX), and they're all just as slow.

When I run ssh -vvv user@host I get the following:
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
<10 second delay>
debug1: Connecting to remotehost [XXX.XXX.XXX.XXX] port 22.
debug1: Connection established.

I don't think this is an sshd configuration issue because our hosts haven't changed.  It doesn't seem that the /etc/ssh/ssh_config changed either.  The only lines uncommented in my ssh_config are the default SendEnv and HashKnownHosts settings (LANG LC_* and yes, respectively).

Any ideas on why this is slow all of a sudden?

---

### Post by minkcar on 2011-10-21
Editing /etc/ssh/ssh_config to include

AddressFamily inet

did the trick.

---

### Post by cleary on 2012-09-18
Thanks for this, fixed the (obscure and difficult to search for) issue for me too :)

---

### Post by lemming465 on 2012-09-28
The underlying cause is probably a DNS issue.  Your ssh client in the absence of 'AddressFamily inet' is probably making an IPv6 AAAA query before it makes an IPv4 A query in DNS.  Since ssh clients aren't yet into the IETF draft "happy eyeballs" mindset, it's not doing these in parallel and going with the first and fastest answer.

If your upstream DNS server has a bad IPv6 setup, it may give a slow timeout in response to the AAAA query instead of a fast NXDOMAIN (assuming the SSH server you are connecting to is still IPv4 only).

So kludging your client to not make AAAA queries is a short term workaround, but the long term solution is to get the DNS server fixed.

---

