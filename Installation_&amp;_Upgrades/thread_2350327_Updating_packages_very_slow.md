---
title: "Updating packages very slow"
date: 2017-01-23
forum: Installation &amp; Upgrades
---

### Post by kevdog on 2017-01-23
Ok -- I guess this is probably a half a questions and half of a rant.  Over the weekend when trying to run:

```
sudo aptitude update && sudo aptitude upgrade
```

Connecting to the ubuntu repository structures seem to take forever.  
My /etc/apt/sources.list is list below.

1. Is anybody else experiencing this?
2. Are there any great mirrors possibly available?  I looked at a few lists however they seemed to lag the main repository by a few days.  I'd like to keep on top of things.
3. Would there be any other reason this process is taking so long?  I have a few ubuntu installs on different machines in my local lan, and they all have this problem.

/etc/apt/sources.list
```

#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                                    #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse


###### Ubuntu Update Repos                                                                    [0/10]
deb http://us.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main

```

---

### Post by ajgreeny on 2017-01-23
Try a different download server instead of the us.archive; maybe the main archive which you seem to think you are already using?

---

### Post by kevdog on 2017-01-23
Hmm -- thanks sorry about the confusion on my part with the archives

Here is a solution but another problem arose.   Here is the solution: 
As found here: [http://askubuntu.com/questions/272796/connecting-to-archive-ubuntu-com-takes-too-long](http://askubuntu.com/questions/272796/connecting-to-archive-ubuntu-com-takes-too-long)

```

Found the solution since it was an IPv6 issue here:

I solved this on 12.10 by editing /etc/gai.conf and uncommenting the line:

#
#    For sites which prefer IPv4 connections change the last line to
#
precedence ::ffff:0:0/96 100
This lets you keep IPv6 enabled, but sets the order of precedence to prefer IPv4 over IPv6.

```

But here is what I get when running sudo aptitude update
```

E: Unable to change to (unreachable)// - chdir (2: No such file or directory)
E: Couldn't clean out list directories

```

---

### Post by SeijiSensei on 2017-01-24
I use the repository archives at MIT since it's near me geographically and topologically. In a GUI software manager choose the "Sources" option and look through the list of alternatives to find one near you.  Universities are typically a good bet.

---

