---
title: "How to open Port 23 for telnet"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2006-12-21
How to open port 23 for telnet 

root@HEX:~# telnet 192.168.1.101
Trying 192.168.1.101...
telnet: Unable to connect to remote host: Connection refused
root@HEX:~# ping 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
64 bytes from 192.168.1.101: icmp_seq=1 ttl=64 time=0.056 ms
64 bytes from 192.168.1.101: icmp_seq=2 ttl=64 time=0.048 ms
64 bytes from 192.168.1.101: icmp_seq=3 ttl=64 time=0.044 ms

--- 192.168.1.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.044/0.049/0.056/0.007 ms
root@HEX:~#

On Windows client
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

c:\temp>telnet 192.168.1.101
Connecting To 192.168.1.101...Could not open connection to the host, on port 23: Connect failed


c:\temp>

---

### Post by darrenm on 2006-12-21
Have you installed telnetd?

---

### Post by moonhk on 2006-12-22
no this package found.

---

### Post by darrenm on 2006-12-22
```
sudo apt-get install telnetd
```?

---

### Post by moonhk on 2006-12-22
I try install inetutils-telnetd, After installed, still have same problem.

---

### Post by MrHorus on 2006-12-22
Don't bother.

Telnet sents data (including usernames and passwords) in plaintext and is nothing but a security liability.

There really is no point in running Telnet when there is SSH - they both allow you to do the exact same thing except SSH is encrypted.

I see you run Windows - Google for "PuTTY" - it's a Windows-based SSH/Telnet client and it's what I use whenever I need to access a remote system from a Windows box.

FWIW the above advice is solid for FTP and POP3 too since both of them are also legacy protocols that send your passwords and data in plaintext.

---

### Post by moonhk on 2006-12-22
Thank. Just install Putty on my PC. It works.

---

### Post by moonhk on 2006-12-22
Just install Cygwin , Openssh file. It works ok. 

c:\temp>ssh
usage: ssh [-1246AaCfgkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-w local_tun[:remote_tun]] [user@]hostname [command]

c:\temp>ssh -l moonhk 192.168.1.101 -p 2222
moonhk@192.168.1.101's password:
Linux HEX 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have mail.
Last login: Fri Dec 22 23:03:08 2006 from 192.168.1.100
moonhk@HEX:~$moonhk@HEX:/tmp$

---

### Post by zain33 on 2008-07-02
> **darrenm said:**
> ```
sudo apt-get install telnetd
```?i want to open port 23 of the destination computer. when i give command of telnet destinaion ip then it says connection failed on port 23. kindly guide me in this respect.

---

### Post by zain33 on 2008-07-02
> **zain33 said:**
> i want to open port 23 of the destination computer. when i give command of telnet destinaion ip then it says connection failed on port 23. kindly guide me in this respect.thanks

---

