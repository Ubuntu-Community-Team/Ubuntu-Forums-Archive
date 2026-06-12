---
title: "Gutsy: apt-get nor aptitude are connecting to repositories"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by dzoner on 2007-11-20
Hello,

I'm having problems with ubuntu server 7.10.

I used aptitude to install some services like courer imap and postfix and everything worked like a charm, but for some reason it just stopped working.

Now I cannot update or install anything via apt-get or aptitude.

Error is that connection is timed out.

```
aptitude update
Err http://security.ubuntu.com gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://cs.archive.ubuntu.com gutsy Release.gpg
  Could not connect to cs.archive.ubuntu.com:80 (147.91.8.38), connection timed out
Err http://security.ubuntu.com gutsy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://cs.archive.ubuntu.com gutsy/main Translation-en_US
  Could not connect to cs.archive.ubuntu.com:80 (147.91.8.38), connection timed out
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://cs.archive.ubuntu.com gutsy/restricted Translation-en_US
  Could not connect to cs.archive.ubuntu.com:80 (147.91.8.38), connection timed out
0% [Connecting to cs.archive.ubuntu.com (147.91.8.38)] [Connecting to security.ubuntu.com (91.189.88.37)]

```

I can ping or resolve both of them properly.

```


ping security.ubuntu.com
PING security.ubuntu.com (91.189.88.37) 56(84) bytes of data.
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=1 ttl=53 time=38.1 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=2 ttl=53 time=41.5 ms

--- security.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 38.139/39.849/41.560/1.722 ms


ping cs.archive.ubuntu.com
PING mirror2.etf.bg.ac.yu (147.91.8.38) 56(84) bytes of data.
64 bytes from mirror2.etf.bg.ac.yu (147.91.8.38): icmp_seq=1 ttl=58 time=1.50 ms
64 bytes from mirror2.etf.bg.ac.yu (147.91.8.38): icmp_seq=2 ttl=58 time=2.23 ms
64 bytes from mirror2.etf.bg.ac.yu (147.91.8.38): icmp_seq=3 ttl=58 time=1.64 ms

--- mirror2.etf.bg.ac.yu ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.500/1.792/2.230/0.317 ms

```

I'm not using proxy of any kind.

Any help would be great.

Tnx

---

### Post by angryfirelord on 2007-11-20
Try going into Synaptic and selecting another mirror.

---

### Post by dzoner on 2007-11-20
> **angryfirelord said:**
> Try going into Synaptic and selecting another mirror.

I'm not using gui of any kind, but I have tried generating new sources list and same thing happens.

It doesn't have matter if I'm using .ca .us or .uk mirrors.

---

### Post by angryfirelord on 2007-11-20
Ok, well then it's a possibility that your DNS isn't working.

[http://ubuntuforums.org/showthread.php?t=519316]("http://ubuntuforums.org/showthread.php?t=519316")
[http://ubuntuforums.org/showthread.php?t=309033]("http://ubuntuforums.org/showthread.php?t=309033")

---

### Post by dzoner on 2007-11-20
> **angryfirelord said:**
> Ok, well then it's a possibility that your DNS isn't working.

[http://ubuntuforums.org/showthread.php?t=519316]("http://ubuntuforums.org/showthread.php?t=519316")
[http://ubuntuforums.org/showthread.php?t=309033]("http://ubuntuforums.org/showthread.php?t=309033")

nope, it's not dns problem because dns is resolving ip adresses properly


I have found error, it was in bad iptables configuration, -i parameter was missing so on default services was loop between interfaces.

Tnx for help

---

### Post by angryfirelord on 2007-11-20
Firewall was my next guess, but it looks like you solved the problem anyway. I'll have to keep this in the back of my mind in case the problem pops up again.

---

### Post by dzoner on 2007-11-21
> **angryfirelord said:**
> Firewall was my next guess, but it looks like you solved the problem anyway. I'll have to keep this in the back of my mind in case the problem pops up again.

the thing is that we hade several networks and network interfaces on the machine, and I didn't look at the firewall script that was writen by another admin, so I took it as granted, but the problem was in it, because all ports were forwareded properly but wihtout -i parameter for incoming interface, so all default ports ftp, web, mysql and so on were in loop, dns was not because it wasn't forwarded, and that explains why resolving of ip addresses was ok

---

