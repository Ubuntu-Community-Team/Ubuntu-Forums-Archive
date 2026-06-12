---
title: "can't install/uninstall packages"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by pdrift on 2011-11-23
I keep getting errors whenever I try to install or remove packages whether it be thru software center, synaptic, or terminal.

I just bought the humble bundle and tried to install thru software center and this is the error I get:

**There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.**

other times, I would get some kind of IO error

my system has been running great up to now, what gives:confused:

I am running 10.10 64 bit, core I3, 8GB of ram

---

### Post by pdrift on 2011-11-30
sorry I've been really busy lately. Just thought i'd post the solution to my problem. at least this is what fixed my problem:

sudo dpkg --clear-avail

---

