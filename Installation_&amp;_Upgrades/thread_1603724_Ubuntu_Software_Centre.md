---
title: "Ubuntu Software Centre"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by ttd82 on 2010-10-23
Hi all,

So I have installed ubuntu 10,04 onto a computer and I am attempting to open the Ubuntu software centre (Applications > Ubuntu Software Centre), I click on it and it opens and closes all within seconds.
It did not do it previously (a few days ago).
I have no idea what to do next
Whats gone wrong?
 can I get some help please.

Thank you very much for your time and assistance

Tom

---

### Post by sikander3786 on 2010-10-23
First of all try,

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

from a terminal and reopen Software Center by,

```
/usr/bin/software-center
```

Does it open now? If not, post the error messages from terminal.

---

### Post by ttd82 on 2010-10-23
Thank you very much for your time and assistance sikander, works much better now!

---

