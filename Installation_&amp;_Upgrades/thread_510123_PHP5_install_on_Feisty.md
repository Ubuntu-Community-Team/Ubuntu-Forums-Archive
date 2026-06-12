---
title: "PHP5 install on Feisty"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by Otaci on 2007-07-26
I can't get PHP5 to install on feisty. I've updated and tried --fix.

Error message is:
```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.1-0ubuntu1.2_amd64.deb  404 Not Found

```

I've checked manually, and the ubuntu1.2 files are not there. There are ubuntu1.4 files. Package directory [http://packages.ubuntu.com/feisty/web/php5-common](http://packages.ubuntu.com/feisty/web/php5-common) indicates 1.4 is the latest version.

Checked package listings in /var/lib/apt/lists and they list 1.2 files. Deleted them all, updated again, still get 1.2 files.

My theory, php5 package updated to 1.4, new package files released, old ones removed. But, package directory listing not updated.

But I'm new to Ubuntu, what do you think? 

Any workaround?

Using this sources.list
```
deb http://security.ubuntu.com/ubuntu feisty main restricted
deb http://security.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
# Ubuntu community supported packages
deb http://security.ubuntu.com/ubuntu feisty universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
```

---

### Post by zanglang on 2007-07-26
The apt listing you have might be a little outdated. Try
> sudo aptitude update
manually? If not, you can wait until the listings get updated, or if you're a little impatient, just download the .deb from the Ubuntu directory link you've posted, that'll work fine as well.

---

### Post by Otaci on 2007-07-26
Thanks, but thats not it. I updated aptitude. Also, the 1.2 files do not exist on the mirror I am accessing, only the later versions exist. I checked some other mirrors and they were the same.

I first tried this a couple of days ago (very imprecise I know, I think it was Monday) and had the same problem. I just thought the mirrors etc might be a bit out of date so I left it and tried again today. No change.

So I dug a bit deeper and checked where I was getting the packages from. To me it really seems like the Package listings are not up to date, so I manually got one from security.ubuntu.com, assuming that they would be the latest versions there. Nope, they also specify version 1.2.

I have finally worked around it though, I Googled for the .deb files, downloaded them manually, then installed. So I've worked around my particular problem, but I think the problem is still present for others.

---

### Post by mburkardt on 2007-07-27
I do have exactly the same problem.

```

apt-get update
apt-get install php5-common

```

fails with this error
```

Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.1-0ubuntu1.2_i386.deb  404 Not Found

```

My /etc/apt/sources.list has the following entries:
```

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

```

Is there a problem with the security.ubuntu.es server?

---

