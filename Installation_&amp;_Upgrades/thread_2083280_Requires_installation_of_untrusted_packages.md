---
title: "Requires installation of untrusted packages"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by quentinl on 2012-11-12
i try to install something in the Ubuntu software center and it says "**Requires installation of untrusted packages"** it gives me 2 options 1 "OK" which just agrees and stops the installation or 2 "repair" which just makes it wait a while before doing nothing i have tried editing the software sources but that does nothing. i am using 12.10 (quantal quetzal) is it something to do with it because i don't think it is in full release yet

---

### Post by Cheesehead on 2012-11-12
There are several possible causes.
For example, you might be trying to pull an untrusted package from a PPA.

We can help you better if you try the instalation in a terminal and give us the exact warning and/or error message.

What package are you trying to install?

Why do you believe 12.10 is 'not in full release yet'? Why do you suspect that's relevant?

---

### Post by vasa1 on 2012-11-12
> **quentinl said:**
> ... i have tried editing the software sources but that does nothing. ...
And unless you know what you're doing, editing the software sources isn't really recommended.

---

### Post by oldos2er on 2012-11-12
Can you post the terminal output from ```
sudo apt-get update && cat /etc/apt/sources.list
```

---

### Post by quentinl on 2012-11-13
> **Cheesehead said:**
> There are several possible causes.
For example, you might be trying to pull an untrusted package from a PPA.

We can help you better if you try the instalation in a terminal and give us the exact warning and/or error message.

What package are you trying to install?

Why do you believe 12.10 is 'not in full release yet'? Why do you suspect that's relevant?

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
has download for 12.04 "[B]For long-term support"
[/B]also i managed to fix it by just changing stuff that seemed right.
and it worked
[http://xkcd.com/627/](http://xkcd.com/627/)
related

---

### Post by coffeepenguin on 2013-10-23
Could you possibly say what you changed, Im having the same problem :/

---

### Post by oldos2er on 2013-10-24
coffeepenguin, instead of bumping old threads, please start a new thread and give as many details about your problem as possible, including Ubuntu version and hardware specs. You have a much greater chance of getting help by doing so.

Old thread closed.

---

