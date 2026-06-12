---
title: "How do I upgrade to Feisty from a different archive"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by lingnoi on 2007-04-20
I want to upgrade to Feisty Fawn using the upgrade manager but I don't want to download the packages from ubuntu.com mirror because it is a lot slower then if I download them from the Thai archive mirror.

I am in Thailand and we have very slow international bandwidth here. I can get Mb/s to anything inside of Thailand but I get Kb/s on anything outside.

Can anyone tell me how I instruct the upgrade manager to download from my local archive instead of the main site?

Thanks,
Andrew :D

---

### Post by GeDaMo on 2007-04-21
The server is specified in the /etc/apt/sources.list file. Make a backup of this (just in case). Edit it, and you should find lines something like
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multive
rse
```
Replace the [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) part in all the lines with [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) and watch the speed to see if it's faster.

I would recommend downloading the alternate CD and updating from that.

---

### Post by lingnoi on 2007-04-23
Just to be clear on this if I change the repositories from

```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
```

to

```
deb http://th.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
```

and then I 

```
sudo apt-get update
```

Then I use the upgrade manager which will download from the Thai Mirror? Because during the upgrade the update manager changes the repositories from Edgy to Fiesty so wouldn't it overwrite this and use ubuntu.com anyway?

Either way I will try this when I get the chance. I just want to be clear for others who want to do this as well.

Thanks,
Andrew :)

---

### Post by GeDaMo on 2007-04-23
Just remember that all the lines beginning with deb have to be changed. If the lines begin with # that means they're commented out and therefore disabled.

---

