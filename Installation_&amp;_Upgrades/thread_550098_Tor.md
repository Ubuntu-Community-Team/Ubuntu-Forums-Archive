---
title: "Tor"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by sctech29169 on 2007-09-13
I am having a problem with TOR, Update Manager, apt-get, dpkg, and Synaptic PM on Feisty. Everytime I try any of these programs, I get a message that says:

Setting up tor (0.1.1.26-1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
chown: cannot access `/var/run/tor': No such file or directory
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have looked at trying to uninstall, then reinstall TOR, but I get a message that says I will have to uninstall Ubuntu Desktop as well.

I have tried apt-get clean and autoremove to no avail.

Any ideas?

Rodeny

---

### Post by Tuho on 2007-11-26
I realise this comes a tad late for you sctech29169, but in case anyone else stumbles upon this issue.

**Quick fix**
Start daemon once, then uninstall.

**Long story**
As the error says, it buggers up in accessing directory '/var/run/tor'. I noticed this "file/directory" was missing altogether. Tried 'sudo touch /var/run/tor' and ended up with the same error. Looked into '/etc/init.d/tor' and found the answer. Tor startup script creates this directory(!) if its not there. Therefore the uninstall script assumes you should always have this directory. In my case, I guess I had installed it, but never got around to using it. I removed the bogus '/var/run/tor' file and started tor daemon and got this: 
```
username@hostname:~$ sudo /etc/init.d/tor start
There is no /var/run/tor directory.  Creating one for you.
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Nov 26 20:30:50.781 [notice] Tor v0.1.1.23. This is experimental software. Do not rely on it for strong anonymity.
Nov 26 20:30:50.854 [notice] Initialized libevent version 1.1a using method epoll. Good.
Nov 26 20:30:50.856 [notice] connection_create_listener(): Opening Socks listener on 127.0.0.1:9050
done.
username@hostname:~$
```
As you can see, tor created the missing directory. After this I succesfully uninstalled tor package.

---

### Post by sctech29169 on 2007-11-26
I want to remind everyone that TOR is NOT secure. In fact, 2600, in a recent podcast suggested that the guy that found out this be "Hacker of the Year"!

When traffic enters the TOR network if it is unencrypted (like email logins) then when it leaves the exit TOR server it can be read by ANYONE that is running or HAS ACCESS to that server.

Thanks Tuho for the post, but based on this "discovery" that is in the MAN I have decided my passwords should remain mine rather than worry about anonymity, I will elect for security.

Thanks

Rodney

---

