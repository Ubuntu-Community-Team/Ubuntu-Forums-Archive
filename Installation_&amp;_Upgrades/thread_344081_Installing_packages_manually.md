---
title: "Installing packages manually"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by itrevorevans on 2007-01-22
Hi, I have just finished installing Edgy on my computer and I'd like to know how I could go about installing ppp and pppoe manually to, obviously, get the internet running and what have you. I need these packages to have the eciadsl driver running.

Thanks in advance.

---

### Post by taurus on 2007-01-22
Skip Section 1 if you don't have internet on that machine.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by itrevorevans on 2007-01-22
> **taurus said:**
> Skip Section 1 if you don't have internet on that machine.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)


Thanks, but here's the deal -- I don't know where I could obtain the pppoe package as a .deb package. [_This page_](http://packages.ubuntu.com/edgy/net/pppoe) has no .deb download link anywhere as far as I could see.

Edit: My bad. I just had to click on i386, not "List of Files." Sorry.

One final question: it appears there's a dependency on libc6. Is that installed by default or should I install it manually as well?

---

### Post by taurus on 2007-01-22
Have you looked to see if those two packages are on the CD?  Then, you can install it directly from the CD with

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ppp pppoe
```

---

