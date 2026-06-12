---
title: "update/upgrade failed"
date: 2013-10-03
forum: Installation &amp; Upgrades
---

### Post by lewjayjr on 2013-10-03
My laptop is running very slow and i ran the sudo apt-get update and then sudo apt-get upgrade.  After everything loaded up in preconfigured the packages and started running.  got this error message:
pkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

Not sure what happened here.  Any help would be appreciated.

---

### Post by ibjsb4 on 2013-10-03
First we need to know what your running.  12.04, 13.04?  And what cpu and how much ram do you have.

Just a shot in the dark, but try these commands.

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by lewjayjr on 2013-10-05
I am running 10.04.  CPU is intel pentium 1.6, GHz, and RAM is 2.0 gig  with 29.9 gig of hard disk available.  This is a Dell Latitude D610

---

### Post by lewjayjr on 2013-10-05
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error  (dpkg configure error)

---

### Post by ian-weisser on 2013-10-05
> **lewjayjr said:**
> dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': [COLOR=#ff0000]Input/output error[/COLOR]  (dpkg configure error)

An input/output error, and slow operation, could mean you have a dying hard drive.
Is your system properly backed up?

---

### Post by raja.genupula on 2013-10-05
here you go , I have found the solution for you
[https://answers.launchpad.net/ubuntu/+question/56777](https://answers.launchpad.net/ubuntu/+question/56777)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8656675](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8656675)

---

### Post by lewjayjr on 2013-10-07
Seems to be working much better now.  Speed picked up and the graying out has stopped.  Thanks for the help.

---

