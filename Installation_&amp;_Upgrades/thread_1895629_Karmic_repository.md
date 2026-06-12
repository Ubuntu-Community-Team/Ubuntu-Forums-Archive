---
title: "Karmic repository"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by jlazkano on 2011-12-15
Hello, I have a old server with Karmic. I need to install a new package, but I notice that my Karmic repository disappear.

Is there any Karmic repository online?

Thanks and best regards.

---

### Post by mörgæs on 2011-12-15
The repository is gone, because Karmic is out of support. 

Have you thought of a fresh install of a supported release?

---

### Post by Lars Noodén on 2011-12-15
[Karmic reached its end](https://wiki.ubuntu.com/Releases) at the end of April this year. You'll probably want to upgrade to a LTS version since that will give 5 years of support.  10.10 (Maverick) will be supported on the server through 2015, but 12.04 when it comes out should be supported through 2017.

---

### Post by jlazkano on 2011-12-15
Hello thanks for your replies.

I know that Karmic is not supported, but I want to know if there is a old repository online. I just need to install one packages.

I will upgrade the 12.04 version.

Thanks and best regards.

---

### Post by waynefoutz on 2011-12-15
> **jlazkano said:**
> Hello, I have a old server with Karmic. I need to install a new package, but I notice that my Karmic repository disappear.

Is there any Karmic repository online?

Thanks and best regards.

try this:

```
gksudo gedit /etc/apt/sources.list
```


comment out every line with a # (or simply remove them)

then add the following lines:

```
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
```


the repositories have been moved here [http://old-releases.ubuntu.com/ubuntu/dists/]("http://old-releases.ubuntu.com/ubuntu/dists/") with all the other EOL releases.

---

### Post by mörgæs on 2011-12-15
> **Lars Noodén said:**
> 10.10 (Maverick) will be supported on the server through 2015

No, 10.10 is supported until april 2012 on both desktop and server.

---

### Post by waynefoutz on 2011-12-15
> **mörgæs said:**
> No, 10.10 is supported until april 2012 on both desktop and server.

I think he meant 10.04, but it's still a 3 year LTS, the first LTS that will have 5 year support will be 12.04.

---

### Post by jlazkano on 2011-12-15
> **waynefoutz said:**
> try this:

```
gksudo gedit /etc/apt/sources.list
```


comment out every line with a # (or simply remove them)

then add the following lines:

```
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
```


the repositories have been moved here [http://old-releases.ubuntu.com/ubuntu/dists/]("http://old-releases.ubuntu.com/ubuntu/dists/") with all the other EOL releases.

Thanks!

This repository works great, I just installed the package.

Best regards.

---

