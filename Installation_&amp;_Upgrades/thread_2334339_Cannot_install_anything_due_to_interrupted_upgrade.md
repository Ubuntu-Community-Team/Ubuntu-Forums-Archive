---
title: "Cannot install anything due to interrupted upgrade"
date: 2016-08-18
forum: Installation &amp; Upgrades
---

### Post by toddpedlar on 2016-08-18
I was upgrading some servers to 14.04 this week (from 12.04) as I eventually wanted to bring them to 16.04, and one got stuck - froze - midway through the installation.  

So - not knowing what else to do, I hard reset the machine, and it came up in a bad state.

The situation is now this.  A partial upgrade was completed, but if I want to complete the upgrade, or to install anything at all, in fact, I am left with only one option - to do a sudo dpkg --configure -a. 

Now when I do this, the installation gets stuck - every time, at "Setting up shared-mime-info (1.2-0ubuntu3)..."

It will sit there forever.

What can be done about this?  The only way I can get out of this stuck position is to kill the dpkg process.  

Any help at all?  Sorry but I've searched all the documentation I can find to no avail. 

Todd

---

### Post by Bashing-om on 2016-08-18
toddpedlar; Ouch .

Have you tried clearing the caches :
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo  apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

Maybe ?

[INDENT][INDENT]get some hope here ?
[/INDENT][/INDENT]

---

### Post by toddpedlar on 2016-08-18
I have done everything except autoclean/clean and didn't think of doing dist-upgrade since I thought that would be something I'd only do with a completely sound build of 14.04.

I'll try these.

---

### Post by toddpedlar on 2016-08-18
Nope.  

Upon trying autoclean (or any of the others)

I get

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

The problem is that if I do this, I end up stuck at the same place, "Setting up shared-mime-info (1.2-0ubuntu3)..."

---

### Post by Bashing-om on 2016-08-18
toddpedlar; Well ..

We get any hints or joy :
```

sudo apt install --reinstall shared-mime-info 

```
per "apt list" that is the correct version for 14.04.
And "apt show" indicates there is no danger to mess about with the package.

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to keep a package manager satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2016-08-18
Rather than just using:

```
sudo apt-get -f install
```

You may want to try the -f or -m suffix with an actual package as target, eg;

```
sudo apt-get install shared-mime-info -f
```

Or:

```
sudo apt-get install shared-mime-info -m
```

Sometimes it's even better to "long hand" the command instead of using just -f or -m. From man apt-get:

```
 -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dpkg --remove to eliminate some of the offending packages).
           Use of this option together with -m may produce an error in some
           situations. Configuration Item: APT::Get::Fix-Broken.

       -m, --ignore-missing, --fix-missing
           Ignore missing packages; if packages cannot be retrieved or fail
           the integrity check after retrieval (corrupted package files), hold
           back those packages and handle the result. Use of this option
           together with -f may produce an error in some situations. If a
           package is selected for installation (particularly if it is
           mentioned on the command line) and it could not be downloaded then
           it will be silently held back. Configuration Item:
           APT::Get::Fix-Missing.

```

Frequently a typical terminal output will reveal that there is a missing (or broken) dependency, so it may say something like trying to configure pkg X but it depends on pkg Y and pkg Y can't be configured because of pkg Z, so you might have to keep trying a combination of the above commands with the name of the actual package until you get to the problem package at the bottom of the pile.

---

### Post by toddpedlar on 2016-08-19
I tried all those things too, except the --reinstall.  But I've already fixed it by looking at a very old thread.   The long and short of it is this:

Removed /var/list/dpkg/updates/*

This unstuck the "have to do dpkg --configure -a" thing

Then I did the following

sudo apt-get remove shared-mime-info
sudo apt-get purge shared-mime-info
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

and miraculously it passed through shared-mime-info without stalling.  Installation seems complete now, finally.

---

### Post by Bashing-om on 2016-08-19
toddpedlar; Outstanding !

You do good work.

As this matter is now concluded -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

