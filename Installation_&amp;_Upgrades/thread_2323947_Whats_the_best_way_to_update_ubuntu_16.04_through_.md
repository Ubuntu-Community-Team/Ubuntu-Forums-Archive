---
title: "Whats the best way to update ubuntu 16.04 through the terminal?"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by tom-bellas3rd on 2016-05-09
Hi all,

I've been looking around but I seem to find alot of different answers for this. How would I go about updating my new install of 16.04 (unity) through the terminal?

The closest I've found on the web was:

sudo apt update && sudo apt full-upgrade

Is this the best way to do it from the terminal?

Thanks in advance!! :)

To clarify, I am not looking to update my old version to 16.04, but to keep 16.04 patched up to the latest security and other patches.

---

### Post by grahammechanical on 2016-05-09
I would not use full-upgrade. You should find that

```
sudo apt update && sudo apt upgrade
```

is sufficient. You will find that apt full-upgrade is does the same as apt-get dist-upgrade. It will remove packages to avoid conflicts. And that has the potential to break the system. It is rare but it can happen. This is what the Apt man page says about apt upgrade & apt full-upgrade:
> 
upgrade (apt-get(8))

           upgrade is used to install available upgrades of all packages currently installed on the system from the sources configured via sources.list(5). New packages will be installed if required to statisfy dependencies, but existing packages will never be removed. If an upgrade for a package requires the remove of an installed package the upgrade for this package isn't performed.

       full-upgrade (apt-get(8))

           full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.

Packages no longer required can be removed by

```
sudo apt autoremove
```

Regards.

---

### Post by poorguy on 2016-05-09
Why not just use the software updater.

---

### Post by QIII on 2016-05-09
Perhaps because, as seems to be the case based on the original post, the OP would like to use the terminal.

---

### Post by vasa1 on 2016-05-09
> **grahammechanical said:**
> I would not use full-upgrade. You should find that

```
sudo apt update && sudo apt upgrade
```

is sufficient. ...
Does *sudo apt upgrade* provide kernel updates? I had the impression that *apt upgrade* (or *apt-get upgrade*) wouldn't.

While it's quite possible that *apt-get dist-upgrade* may break the system, I've been using it for a couple of years without my noticing it misbehave.

---

### Post by poorguy on 2016-05-09
> **QIII said:**
> Perhaps because, as seems to be the case based on the original post, the OP would like to use the terminal.

I was asking a general question to see if updating using the software updater was any different than updating using the terminal.

It wasn't directed @ the OP although it does seem that way.

---

### Post by vasa1 on 2016-05-09
> **poorguy said:**
> I was asking a general question to see if updating using the software updater was any different than updating using the terminal.

It wasn't directed @ the OP although it does seem that way.
It's better to formulate your *own* question in your *own* thread in the appropriate area. Otherwise, there's a chance of derailing another's poster's thread and that may not be advisable.

---

### Post by tom-bellas3rd on 2016-05-10
> **poorguy said:**
> Why not just use the software updater.

I did a fresh install on a system last night and after the initial batch of updates and a reboot my system kept notifying me that more updates were ready. I would click on the software update button but it came up saying everything was complete. 

After running the command line 
sudo apt update && sudo apt upgrade

I was able to install the last updates, which were some AMD updates. Not sure why it wouldnt work through the GUI interface, but it finally
was able to complete. 


TY all that responded.

---

### Post by grahammechanical on 2016-05-10
> Does *sudo apt upgrade* provide kernel updates? I had the impression that *apt upgrade* (or *apt-get upgrade*) wouldn't.

The answers are, Yes & Not so. Yesterday I did some work on a fresh install of Yakkety Yak and as I was going to install packages using the terminal I first updated/upgraded using the terminal and the update brought in a kernel upgrade. Which brought that installation up to date with another install of Yakkety that got the same kernel upgrade through Software Updater.

Also in 16.04 apt autoremove will remove previous kernels leaving just the two newest kernels. In the past autoremoved only remove each previous kernel one at a time. 

Regards.

---

