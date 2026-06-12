---
title: "How do I &quot;lock&quot; a package with Adept?"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by vr04 on 2007-01-13
I compiled gaim2.0beta5 from source, however Adept thinks that gaim 1.5 from the repos is the newer version. If I do a sudo apt-get dist-upgrade, it'll "update" to gaim 1.5.

My question is, how do I "lock" the compiled gaim version as the one that I want to keep with Adept? (I'm using Kubuntu). I know that Synaptic has an option to lock packages.

---

### Post by markster23 on 2007-01-13
that's a good question.. i noticed that if u look a package version in synaptic, adept-notifier still tries to upgrade it.. :/ crappy deal heh

---

### Post by vr04 on 2007-01-14
Does anyone have a suggestion?

---

### Post by vr04 on 2007-01-16
bump

---

### Post by Divan Santana on 2007-01-27
Adept probably doesn't have that feature.

For Edgy Synaptics lock version for a package doesn't seem to work. :(

---

### Post by Clouseau on 2007-02-01
I use Edgy and I noticed that I cannot run Adept re: "Failed to execute child process "kdesu" (No such file or directory)" Is this an Edgy issue or something else? Not sure if this is related, but I noticed an Adept issue. Sorry if I am out of line.:)

---

### Post by dannyboy79 on 2007-02-01
it's called "hold". just do man aptitude and read all about it.

---

### Post by Clouseau on 2007-02-02
does this apply to Adept also?

---

### Post by vr04 on 2007-02-04
I've tried "sudo aptitude hold" without luck. Aptitude-notifier (or whatever it's called) still tries to install 1.5.

---

### Post by JDahl on 2007-02-04
Do like one of the parent replies suggested - use "hold".

In aptitude use "?" to get help,  which tells you to use "=" to hold a package.

That some of these features stopped working in Edgy Eft is utter nonsense; Ubuntu
doesn't customize the Debian package manager.

---

### Post by dannyboy79 on 2007-02-05
according to man apt-get:
 --ignore-hold
              Ignore  package  Holds;  This  causes  apt-get  to ignore a hold
              placed on a package. This may  be  useful  in  conjunction  with
              dist-upgrade to override a large number of undesired holds. Conâ
              figuration Item: APT::Ignore-Hold.

       --no-upgrade
              Do not upgrade packages; When used in conjunction with  install,
              no-upgrade  will prevent packages on the command line from being
              upgraded if they  are  already  installed.  Configuration  Item:
              APT::Get::Upgrade.

or have you just tried using the gui synaptic or whatever it's called? I am sure there is some feature to hold a package so it doesn't get updated.

---

### Post by tagra123 on 2008-07-03
LOCK / PIN a package in Adept using apt/preferences


A quick way is to copy the contents of

/var/lib/synaptic/preferences

to /etc/apt/preferences

this makes adept behave (lock the same packages as synaptic)

Of course you have to use synaptic originally to lock the version.

You can also see   info apt_preferences to learn more

---

