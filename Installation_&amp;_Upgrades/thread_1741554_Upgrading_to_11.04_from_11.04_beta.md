---
title: "Upgrading to 11.04 from 11.04 beta"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by ias0nas on 2011-04-28
Hello,

I have the 11.04 beta installed. Is going to final 11.04 just a question of updating through Update Manager?
Or do I have to do something else?

How do I check I am which version I am using? In the about menu it says "You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011"

Thanks,
Jason

---

### Post by Irihapeti on 2011-04-28
If you have been keeping it updated, then you already have 11.04.

Enjoy!

---

### Post by vanadium on 2011-04-28
It is a matter of keeping your system updated.

---

### Post by KegHead on 2011-04-28
Hi!

You'll be notified.

I completely update via;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

KegHead

---

### Post by vanadium on 2011-04-28
I just used
```

sudo apt-get update -d

```
and it worked quite nicely. I usually do a full fresh install, but I was eager to test Unity two weeks ago. I feel inclined to leave my principles behind and continue this way of upgrading ;)

---

