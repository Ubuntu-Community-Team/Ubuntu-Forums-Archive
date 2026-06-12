---
title: "dpkg: parse error, in file `/var/lib/dpkg/available'"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by happy-and-lost on 2007-03-21
OK, full error:

```
jo@mithos:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  fortune-mod fortunes-min python-gst0.10 wesnoth wesnoth-data wifi-radar wine
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/37.6MB of archives.
After unpacking 614kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: parse error, in file `/var/lib/dpkg/available' near line 100 package `sun-java5-jre':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I've had a look at my /var/lib/dpkg/available file, and there are bits missing all over the place, I guess it's corrupted. I couldn't open .../available-old, and cat-ing it revealed noting but "&#9229;1&#9618;&#9618;&#9226;0&#9618;1°6 2.0.0.1&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;-1 1" and such like.

Any ideas as to what to do?

(Feisty Fawn, by the way)

Quick Afterthought: After a spot of Googling, this seems to be an old Debian issue, but was fixed back in the Debian 2.x days. Maybe a b0rked FF update caused this?

---

### Post by denver on 2007-03-21
try using

```
sudo apt-get update
sudo apt-get upgrade
```

first and see if that helps.
apt caches the packages and package versions in a local file for fast searching. It might be that you haven't updated it in a while and apt is looking for an older version of the package on the server. ( i might be wrong but there is no harm in trying )

---

### Post by LegoAddict on 2007-04-11
I am having the same (or similar) problem.

I ran the code you told me to run, and that was fine.

Then I see some updates in the Update Manager.  I download them and install, to get this error in the little terminal thing:

dpkg:  Parse error, in file 'var/lib/dpkg/available' near line 1:
Newline in field named 'padding'
E:  Sub process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

This is getting extremely annoying.  I can't install anything!

---

### Post by Zorro on 2007-04-22
*bump*

Anyone have/know of a solution?

---

### Post by Zorro on 2007-04-22
Found the 'fix' just * sudo rm /var/lib/dpkg/available *  and do an apt-get update and all is good...

---

### Post by CypherDelic on 2007-12-18
> **Zorro said:**
> Found the 'fix' just * sudo rm /var/lib/dpkg/available *  and do an apt-get update and all is good...


This gets me to this:leting available

dpkg: Konnte Paket-Infodatei »/var/lib/dpkg/available« nicht zum Lesen öffnen: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
cypher@HaeckFlaisch:~$ 

I run sudo apt-get update and upgrade after de

---

### Post by mchibuco on 2007-12-19
I am new to Ubuntu... this is my first post ever, so I hope it is helpful.

I had the same problem with the message:

dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

Then I noticed that there was no file called /var/lib/dpkg/available. However there was a file called "available-old" in that directory. I am not sure how that got there, but I assume that somehow during my various tinkering around, the "available" file was deleted.

My fix was to recreate the "available" file by typing at the prompt:

$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available

Then I did the apt-get steps again:

$ sudo apt-get update
$ sudo apt-get upgrade

It worked! :) When I said "Y" to the upgrades, they occurred smoothly with no error messages. Now I only wonder if someone with experience could explain if my "fix" is acceptable, so I am not misleading anyone. :confused:

---

### Post by lone_deranger on 2008-01-28
I had the same problem, and tried what was mentioned, but it didnt work.
On launchpad I found this command, which worked great, and updated without problems.

sudo dpkg --clear-avail && sudo apt-get update

---

### Post by jcook on 2008-02-04
I had the same problem and tried all the suggestions. The "sudo dpkg --clear-avail && sudo apt-get update" suggestion finally worked. Thanks!

---

### Post by markus211 on 2008-02-10
same for me all other solutions on this page did not cause any change but this did? 
anyone no why?


i mean "sudo dpkg --clear-avail && sudo apt-get update" why would this work and not everything else?

---

