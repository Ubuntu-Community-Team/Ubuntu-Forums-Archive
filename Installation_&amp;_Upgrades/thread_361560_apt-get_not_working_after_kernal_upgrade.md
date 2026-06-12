---
title: "apt-get not working after kernal upgrade"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by 15index on 2007-02-14
I am satisfied with the way Ubuntu has been working for me. I installed Dapper last year and all was well. Last week there was a kernal update to: kernal 2.6.15-28-386. Since then, I cannot use apt-get update to work.

After some limited research, I found a tread that said to type in "export http_proxy=http://[proxy_address]:[port]" (the quotes are mine). Apt-get will work after that until I close the terminal. When I reopen the terminal, I have to re-enter the "export" command.

Synaptic was doing the same thing until I change the network proxy setting to the correct one. Now Synaptic works every time.

Where do I add the proxy information so that I can run from the terminal. I like the idea of using apt-get and aptitude when possible.

---

### Post by bapoumba on 2007-02-14
Hi,
were you behind a proxy before the upgrade ? Your settings should not have changed.
What it the output to **cat /etc/apt/apt.conf** ?

---

### Post by 15index on 2007-02-17
I've been away for a couple of days. My /etc/apt/apt.config is empty. What needs to go in there? 

I use a proxy and as I stated, when I set up the proxy in Synaptic, it works.

---

### Post by bapoumba on 2007-02-17
> **15index said:**
> My /etc/apt/apt.config is empty.
/etc/apt/apt.conf (not config ;))

---

### Post by 15index on 2007-02-18
My mistake! I meant /etc/apt/apt.conf is empty.

Thank you for being patient and trying to help me resolve this issue.

---

### Post by bapoumba on 2007-02-18
No problem.
[http://www.die.net/doc/linux/man/man5/apt.conf.5.html]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html")
What you want to look at is the acquire group.
```
ACQUIRE { 
http://[[user][:pass]@]host[:port]
};

```
here is mine:
```
ACQUIRE { 
http::proxy "http://myproxy.myhost.fr:xxxx"
};

```
I do not need identification.

---

### Post by 15index on 2007-02-18
This is what I like about Ubuntu. I had a problem and someone came along and pointed me in the right direction.

With your help, I was able to get things running the way I wanted.

Many Thanks!

---

