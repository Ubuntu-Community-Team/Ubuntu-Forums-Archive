---
title: "apt-get upgrade doesn't install all updates"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by stlu on 2012-07-24
Hello,

I prefer to use *apt-get upgrade* over the GUI package "update-manager".  Recently I noticed that there are packages in update-manager with the tag "(New install)" which *apt-get upgrade* does not fetch. 

How can I get apt-get upgrade to perform this action?

---

### Post by plucky on 2012-07-24
> **stlu said:**
> Hello,

I prefer to use *apt-get upgrade* over the GUI package "update-manager".  Recently I noticed that there are packages in update-manager with the tag "(New install)" which *apt-get upgrade* does not fetch. 

How can I get apt-get upgrade to perform this action?

```
sudo apt-get dist-upgrade
``` and see what that does for you.

Good Luck

---

### Post by stlu on 2012-08-09
Thanks,

This command also solves my confusion over some packages being "held back" when I used *apt-get upgrade.*

---

### Post by drmrgd on 2012-08-10
Just for more information, here's a quick article about why you sometimes see packages as being held back:

[http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69)

Anytime you want to pull the trigger and get those packages, all you need to do is run 'dist-upgrade' instead.

---

