---
title: "Update Manager : Failed to download repository information"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by jamesallen4u on 2012-09-29
Hello everyone,

For the past week, whenever I try to update via the Update Manager, I get the following errors: 

```
[W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Here is the screenshot:

[IMG]http://i.imgur.com/ZzCL7.png[/IMG]

My internet connection works perfectly as I am able to access this forum. I don't understand the sources of these errors since I am still learning to use Ubuntu. Please help me out with this error. Thanks in advance for your help.

---

### Post by jerrrys on 2012-09-29
Looks like the [PPA for Precise 12o4]("http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/") no longer exist.

You need to either remove it or comment (#) it out in your software [sources.list and/or your sources.list d.]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+edit+sources+list&as_qdr=all&sa=Google+Search&lang=en")

And welcome to the forum :)

---

### Post by jamesallen4u on 2012-10-02
Thank you for your reply, all errors have been fixed. Marked as solved.

---

### Post by jerrrys on 2012-10-02
Welcome :)

---

### Post by jamesallen4u on 2012-10-02
Thanks :)

---

