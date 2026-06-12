---
title: "Help!!!! Ubuntu cannot boot. Stopped upgrading 1/2 way through"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by Info101 on 2011-12-23
Hi.

I had to swith off my pc halfway through upgrading from 9.10 to 10.04.3 and now I can't boot into ubuntu. It just shows a bunch of mounting errors and DRDY errors.

I've somehow navigated to manual recovery and after entering password I try "sudo apt-get upgrade --fix-missing" but then I get some could not resolve "my.archive.ubuntu.com" error.

It still tries but after a while it just stays at "Processing triggers for python-support......" and it also says that it failed to fetch a bunch of files.

Please help!

---

### Post by c5wagner on 2011-12-23
You're swap space might not have switched over. It is also suggested to back everything up before upgrading and do a fresh install.

---

### Post by Info101 on 2011-12-23
How do I backup when I can't even access? Sorry, I'm kinda slow.

---

### Post by c5wagner on 2011-12-23
Well you should have backed up before, what i suggest now is booting a live cd and backing up you're files to an external drive then doing a fresh install.

---

### Post by Info101 on 2011-12-24
This is kind of a stupid question but is there a way I can copy/paste my main hdd(sda) to an external hdd(sdc) through command line?

You know for backup.

---

### Post by c5wagner on 2011-12-24
It depends what you're doing, if you're able to get a command line with your unfinished OS, then try these first 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

