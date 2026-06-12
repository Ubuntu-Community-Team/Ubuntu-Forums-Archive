---
title: "apt: package `ksysguard' is missing final newline"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by george@reilly.org on 2006-07-13
ksysguard is thoroughly messed up and preventing just about all other apt-related activities.

[INDENT]E: /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.2_i386.deb: files list file for package `ksysguard' is missing final newline
[/INDENT]
I've tried blowing away this file and reinstalling it. It didn't help. I even tried *sudo dpkg-reconfigure -a*, which led me to see lots of ELF warnings about libksgrd.so.1:

[INDENT]$ head /usr/lib/libksgrd.so.1.2.0
]=Faydal&#305; Kiñä&#351;lär
GenericName[uk]=&#1050;&#1086;&#1088;&#1080;&#1089;&#1085;&#1110; &#1087;&#1086;&#1088;&#1072;&#1076;&#1080;
...[/INDENT]

I'm not sure how I got into this state, but I think it all started when I tried to get beagle through Synaptic.

---

### Post by abethke on 2006-08-08
I have this problem too, and it is crippling my computer.  Not being able to use apt is not good!  Does anyone have a solution?

---

### Post by hordur on 2006-10-19
Hello.

I had a similar problem with another package.
I spent a lot of time trying to fix and I finally managed to do it.
Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

I don't know if all the steps are necessary, maybe 1 and 4 are enough.

---

### Post by berryjw on 2007-01-28
> **hordur said:**
> Hello.

I had a similar problem with another package.
I spent a lot of time trying to fix and I finally managed to do it.
Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

I don't know if all the steps are necessary, maybe 1 and 4 are enough.


Short story - 1 and 4 are enough.  Long story...

I was having this problem with gzip, which prevented updates from installing.  I opened a terminal, entered 'sudo gedit' to do step 1 (remove the gzip reference), then entered the two steps in 4.  Re-executed the updates, and things worked perfectly.
 
Important notes
You have to have root access to /var/lib/dpkg/status, or you can't save it, hence starting it from a terminal using sudo/gedit
Step 4 is *two* lines, 'apt-get update' and 'apt-get -f install'.  Run them one after the other.
Also, /var/lib/dpkg/status is very large - I used gedit for it's search window (couldn't remember how to search in vi, too many years...) to find the gzip listing (at line 17352).  
There are several other references to 'gzip', you're looking for a block headed with it.  If you're having problems with a different package, find (and delete) the section headed with that package name.  For my own sense of security, I cut and pasted it into another document and noted the location in the file, so I could put it back if something broke.

Bj

---

### Post by Bataille23 on 2008-04-09
> **hordur said:**
> Hello.

I had a similar problem with another package.
I spent a lot of time trying to fix and I finally managed to do it.
Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

I don't know if all the steps are necessary, maybe 1 and 4 are enough.

I was having the same problem, and I PANICKED.  I just had to get on here and thank you, because you saved me a letter grade in one of my classes.  Had I not fixed it, I would've obsessed over it and neglected my paper.

---

