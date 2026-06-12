---
title: "Why can't I install telnetd???"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by AlliumPorrum on 2006-07-03
I need telnet daemon to be able to use MySQL administration tools from remote computer. I tried to install telnetd, but none of these works:

sudo apt-get install netkit-inetd
sudo apt-get install telnet
sudo apt-get install telnetd

I always just get the error "Couldn't find package...". 

How can I install the telnet server??

---

### Post by th3james on 2006-07-03
Have you tried searching for it in synaptic? or try

apt-cache search telnet

---

### Post by AlliumPorrum on 2006-07-03
No I haven't because I'm running a server without a desktop...

I tried that search, and it gives me just:

jasurakk@jasurakk-dell:/etc$ apt-cache search telnet
libcommons-net-java - internet protocol suite Java library
libident - simple RFC1413 client library - runtime
liblog4j1.2-java - Logging library for java
libssl0.9.8 - SSL shared libraries
libwrap0 - Wietse Venema's TCP wrappers library
libwrap0-dev - Wietse Venema's TCP wrappers library, development files
python2.4-twisted-bin - Event-based framework for internet applications
python2.4-twisted-core - Event-based framework for internet applications
tcpd - Wietse Venema's TCP wrapper utilities
telnet - The telnet client
twisted-doc - The official documentation of Twisted

So no telnetd in here?? What the heck...?

---

### Post by mbailey on 2006-07-03
Can you use ssh instead?

---

### Post by dcroal on 2006-07-03
Looks like you have to enable the universe repository, see
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=telnetd&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=telnetd&searchon=names&subword=1&version=dapper&release=all)

Be careful using it, it's not considered to be very secure.

---

### Post by AlliumPorrum on 2006-07-03
> Looks like you have to enable the universe repository, see
[http://packages.ubuntu.com/cgi-bin/s...er&release=all](http://packages.ubuntu.com/cgi-bin/s...er&release=all)

Thanks, but I'm not so used to Linux yet, so could you please tell me how to do this from CLI??

About SSH, I surely would like to use it, but it seems that telnet is only possibility with MySQL admin & query tools. Anyway my client and server are located on the same subdomain behind my own firewall, so this shouldn't be a big problem. And this is really only for my personal purposes, not for any public internet site or something like that.

---

### Post by houstonbofh on 2006-07-03
You are looking for "inetutils-telnetd" and you will need to edit your sources list with *sudo nano /etc/apt/sources.list* to enable "universe" repositories.

---

### Post by AlliumPorrum on 2006-07-04
I managed to install both telnetd and inetd, but still telnet server won't work. I don't see 'telnetd' on the process list, and 'telnet localhost' wont work either. What should I do next??

---

### Post by houstonbofh on 2006-07-04
I have not installed or used this package, so I am shooting in the dark here...  First reboot.  If a startup script was installed, it should run.  If not, from the desktop go to System-->Administration-->Services and see if it is there.  If not, you will need to find out how to run it manually.

---

### Post by AlliumPorrum on 2006-07-04
Well I'm running Ubuntu without desktop, so unfortunately that does not help much. If I run 'telnetd' from CLI, it seems to do something because any errors won't appeat. Telnetd won't be on the process list anyway.

If I now do 'telnet localhost' , I have this kind of response:

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
 
So it seems that something is happening, but is this what really should happen?? Connection from the MySQL admin tool won't work anyway...

---

