---
title: "Server Install Problem"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by zonkwilliams on 2008-10-16
I am setting up a server to run Cacti on and I am having trouble with the proxy setting. When I run sudo apt-get update a line pops up saying "connecting to Webproxy" but there are two of them in the same line? I can download about half of the updates but when I run sudo apt-get upgrade nothing gets installed or upgraded? I am guessing that the needed packages are not being downloaded since it errors out about halfway through.
I got around our proxy by using "export http_proxy=http://webproxy/scripts/inet.pac" since our proxy has existing scripts it run for setup. Do I need to try the [http://username](http://username) password @ IP : port?
Thanx

---

### Post by cariboo on 2008-10-16
I'm not sure what you mean when you  say:

> I can download about half of the updates but when I run sudo apt-get upgrade nothing gets installed or upgraded? I am guessing that the needed packages are not being downloaded since it errors out about halfway through

When you run:

```
sudo apt-get update
```

All the command does is uodate the paclage list to actually download and install the update you have to run:

```
sudo apt-get upgrade
```

If you get an error when downloading the updates try:

```
sudo apt-get install -f
```

the **-f** stands for **fix missing**

Jim

---

