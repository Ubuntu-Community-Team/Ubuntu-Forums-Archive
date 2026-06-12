---
title: "Ubuntu hangs after 2.6.31-17-generic update"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by euxneks on 2010-01-09
Hello all. I did an update recently and it won't continue booting past a certain point - which I think is rather strange, the last message I can manage to see is:
```

 * Starting init crypto dicks...

```

No. That's not a typo. I couldn't believe my own eyes - I took a picture:
[http://www.flickr.com/photos/euxneks/4258018837/](http://www.flickr.com/photos/euxneks/4258018837/)

I can guarantee you this is not a joke. I suspect my video card is aging on me as I get a 'London Pound" symbol on my CLI terminal sometimes.

Anyway, that's not the real issue for me. I cannot start into 2.6.31-17, but I can start into 2.6.31-16 - is anyone else having this problem?

Edit: Restarting doesn't give me the crypto dicks thing but I still get another common error:
```

init: ureadahead-other main process (###) terminated with status 4

```

Thanks!

---

### Post by yankee83 on 2010-02-14
I have the same problem at the moment. Were you able to solve it?

---

### Post by euxneks on 2010-02-14
> **yankee83 said:**
> I have the same problem at the moment. Were you able to solve it?

Unfortunately, not. However, doing a clean install of Ubuntu 9.10 solved all issues I had encountered. :\ Kinda crappy that I was only able to solve with a complete reinstall - oh well :)

---

### Post by yankee83 on 2010-02-14
Actually it turned out that the ureadahead warning was harmless but more important was an error coming from the network interfaces. I had a syntax error in /etc/network/interfaces which prevented the system from booting. The bug is described here: [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253)

---

### Post by yankee83 on 2010-02-14
Here is also a solution that might fix the ureadahead problem:
[http://tech--help.blogspot.com/2009/12/ubuntu-solved-ureadahead-other-main.html](http://tech--help.blogspot.com/2009/12/ubuntu-solved-ureadahead-other-main.html)

---

