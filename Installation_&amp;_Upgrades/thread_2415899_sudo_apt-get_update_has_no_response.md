---
title: "sudo apt-get update has no response"
date: 2019-04-02
forum: Installation &amp; Upgrades
---

### Post by vlvanchin on 2019-04-02
Dear Team,

The below command does not execute, it takes a very long time , the version of Ubuntu is 16.04

```
$ sudo apt-get update 

```
It process hangs with the following:
```

Hit:1 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial InRelease
Hit:2 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) xenial InRelease                                      
Hit:3 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease   
Ign:4 [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) xenial InRelease
Ign:5 [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) xenial-updates InRelease
0% [Waiting for headers] 

```
I also tried with the ubuntu main server in the software update settings... still the same.

Can anyone help me out, please?

Thank you

vanchin

---

### Post by Rubi1200 on 2019-04-02
Hi and welcome to the forums :-)

It seems there might be some issues with the Ubuntu repos:

[https://twitter.com/UbuntuBot2075](https://twitter.com/UbuntuBot2075)

Scroll through to see quite a few mentions of similar issues.

Hope this helps.

---

