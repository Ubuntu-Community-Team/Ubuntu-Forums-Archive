---
title: "linux-generic linux-restricted-modules-generic kept back"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by dwiel on 2008-09-08
with every apt-get upgrade I get the following message:

```
The following packages have been kept back:
  linux-generic linux-restricted-modules-generic

```
I have also tried dist-upgrade:

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

$ uname -a
Linux dwiel 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```
This has been happening for a while now.  I've had the problem in the past and it would only last a day or two.  This has been going on for at least a month now.

I have also tried:

```
$ sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-generic: Depends: linux-image-generic (= 2.6.24.21.23) but 2.6.24.19.21 is to be installed
                 Depends: linux-restricted-modules-generic (= 2.6.24.21.23) but 2.6.24.19.21 is to be installed
E: Broken packages

```
These packages also show up in the graphical Update Manager, but are greyed out and never get installed.

Thank you!

---

### Post by lifestream on 2008-11-24
I had the same answer, and can tell you that the reason 
**[COLOR="Red"]Please[/COLOR]** use google search before creating a new thread, I did a google search for that same question just now, and found:
[http://ubuntuforums.org/showthread.php?t=851584](http://ubuntuforums.org/showthread.php?t=851584)


To help you learn google search: For this example, I used the search terms:
> ubuntu apt-get kept back 
Which is what the problem is, right? Right. 
The first 4 google results had the answer to my question -- and yours.

That's probably why no one has answered this so far. 

Rant over.
-----------------------------------------------------------------------
Linux kernel is being kept back because the necesary packages to satisfy l*inux-generic* have not yet been added to the repositories.

---

### Post by SeaWeedz on 2011-08-16
I searched "apt-get upgrade linux-generic" and found this thread.. 

the right thing to do now would be to write what the actual procedure is, because I'm sure the next person will come along wanting this resolved..  but ah I'm tired.

---

### Post by littelbro14 on 2011-12-31
The guy above me must be psychic. This was the first result when I googled the same problem. Instead of ranting about people not knowing how to google, try giving an actual answer, so when people do google, they can find the answer.

---

### Post by abarth on 2012-02-15
You will find a solution here: [http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69)


In short, "apt-get upgrade" does by default not install new packages which might be necessary to upgrade to new versions of your installed ones.

To upgrade all packages, you can use:

```
sudo apt-get dist-upgrade
```

This solved the problem in my case.
If this does not work for you, then you can explicitly install the package who are hold back:

```
sudo apt-get install <packages>
```

---

