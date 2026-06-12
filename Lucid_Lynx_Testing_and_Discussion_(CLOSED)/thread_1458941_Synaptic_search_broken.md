---
title: "Synaptic search broken?"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by StuartN on 2010-04-20
I wanted to install Thunderbird in the release candidate, but it did not appear when I searched. I then tried a few other packages, both installed and uninstalled. No matter how I search, I seem unable to locate some packages - as if some filter is already in place.

(Thunderbird is in the list and does install.)

---

### Post by wilee-nilee on 2010-04-20
> **StuartN said:**
> I wanted to install Thunderbird in the release candidate, but it did not appear when I searched. I then tried a few other packages, both installed and uninstalled. No matter how I search, I seem unable to locate some packages - as if some filter is already in place.

(Thunderbird is in the list and does install.)

I see you have a lot of beans so I am sure you are aware of ticking on some extras repositories. Also synaptic will sometimes not find things with the quick search, so you have to click the search icon and find them that way.

A apt-get from the terminal will install whatever is available though.

---

### Post by StuartN on 2010-04-21
> **wilee-nilee said:**
> Also synaptic will sometimes not find things with the quick search, so you have to click the search icon and find them that way.

Perhaps I was not clear - the package is available and it is listed in Synaptic Package Manager. I do not wish to scroll down to it, so I search. The search does not find the package, the search is broken.

---

### Post by dino99 on 2010-04-21
work fine on my end. So you can reconfigure synaptic or remove/purge it then reinstall

---

### Post by seeker5528 on 2010-04-21
> **StuartN said:**
> Perhaps I was not clear - the package is available and it is listed in Synaptic Package Manager. I do not wish to scroll down to it, so I search. The search does not find the package, the search is broken.

You still didn't say how you were searching.

It works for me if I type 'thunderbird' in the quick search.

Or if I select all on the left, click on any package in the package list, then type 'thunderbird'.

Or if I click search, type 'thunderbird' as the search term and have 'name' or 'description and name' selected in the 'look in' box. 

But if I search and have 'provided packages' selected in the 'look in' box, then I get some thunderbird related packages, but not thunderbird itself. Which is expected since what thunderbird provides is 'mail-reader'.

Later, Seeker

---

### Post by wilee-nilee on 2010-04-21
> **StuartN said:**
> Perhaps I was not clear - the package is available and it is listed in Synaptic Package Manager. I do not wish to scroll down to it, so I search. The search does not find the package, the search is broken.

I did not suggest you scroll to anything.

Have you installed any repositories then ticked them off. The PPA for Ubuntu Mozilla Daily Build Team is what I am curious about this ppa provides the 3.0 & 3.1 versions of Thunderbird. Have you tried both types of search available in synaptic?

So if you feel that the search is broken a purge and reinstall of synaptic as suggested is where I would start.

Your problem is unusual and I would see more threads a couple of months ago about Ubuntu software center problems.

---

### Post by StuartN on 2010-04-26
I see that this bug has been reported on Launchpad (with plenty of duplicates) - [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797?comments=all](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797?comments=all)

The bug seems to persist in 10.04

---

### Post by dino99 on 2010-04-26
agree with a strange logical search: for example search a common name as "gnome":

the result is not listed in alpha mode, wonder on which colomns it create its index: package+details, might indexed only on package name

---

