---
title: "medibuntu.org"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by bstanley on 2008-09-22
Since last Friday,

Every time I run update manager the following repository gets a 
time out error message:

  packages.medibuntu.org/dist/hardy/Release.org


  (both  free and non-free links).

I if google  medibuntu.org and try to connect that way,  no connection
occurs.

Is there a problem with the   medibuntu.org server(s) ?

---

### Post by fballem on 2008-09-22
Sorry, but I don't get the problem. Having said that, it might be worth re-initialising your links, on the off-chance that the problem is there. If you don't know how to do that, then please open a Terminal, and enter the following two commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Hope that this helps,

---

### Post by Yannick Le Saint kyncani on 2008-09-22
> **bstanley said:**
> Is there a problem with the   medibuntu.org server(s) ?

Hi bstanley,

Just now, from apt-get update :

```

Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://packages.medibuntu.org hardy/free Sources
Hit http://packages.medibuntu.org hardy/non-free Sources

```

No problem whatsoever.

---

### Post by bstanley on 2008-09-23
I just went to the  [www.mediubuntu.org](www.mediubuntu.org) website using Firefox.

I then clicked on their Packages link and it timmed out
(server taking to long to respond).

I tried seveal times with the same results.

This did work ok this morning.

It seems their are having problems in the late afternoon
or are probably just being swamped with users.....

---

### Post by keyshawn on 2008-09-25
I am experiencing the same problem as well: I'm unable to reach the medibuntu (through wget or through a web browser at all 
(today was the first time that I ever tried and I've continued to have problems for the past 6 hours).

---

### Post by crazee64 on 2008-09-25
I am also having problems - can't resolve medibuntu.org at all! Are they having DNS problems? Perhaps relocating to another ISP or something? I was on yesterday - went to put the same software on another PC today and not seeing medibuntu.

---

### Post by msfraser on 2008-09-25
Also having DNS issues here...

nslookup [www.medibuntu.org](www.medibuntu.org)
Server:         139.130.4.4
Address:        139.130.4.4#53

** server can't find [www.medibuntu.org:](www.medibuntu.org:) SERVFAIL

---

### Post by drekbour on 2008-12-26
Also having DNS issues with medibuntu.  The test was simply to use a named external dns server to prove the default one (the ISP's) was incorrect:
$ dig medibuntu.org
; <<>> DiG 9.5.0-P2 <<>> medibuntu.org
;; global options:  printcmd
;; connection timed out; no servers could be reached
$ dig @resolver1.opendns.com medibuntu.org
<... works fine>

Email your ISP to update their DNS.

---

### Post by nlz on 2008-12-26
same problem here, right when i'm installing ubuntu onto someone's PC.. **nice** NOT!

---

### Post by drekbour on 2008-12-27
Users can change the resolv.conf settings to use avoid the ISP's DNS server.  See all of this thread:
[https://answers.launchpad.net/ubuntu/+question/2248](https://answers.launchpad.net/ubuntu/+question/2248)

---

