---
title: "Intallation of GIMP on Ubuntu 10.4"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by haunted house on 2012-02-26
I have installed Ubuntu 10.04 and applied updates as detailed in [http://www.futuredesktop.org/](http://www.futuredesktop.org/).

I think this means I effectively have 11.10 with KDE desktop.

When I attempt to install GIMP from Ubuntu Software Center/Get Software I get the following message


installArchives() failed: dpkg: configuration error: /etc/dpkg/dpkg.cfg.d/multiarc:1: unknown option 'foreign-architecture' 

Why is it failing?

---

### Post by sidzen on 2012-02-26
Applying this code in 10.04  (Lucid Lynx), taken directly from that page you linked to.
[PHP]sudo wget http://www.medibuntu.org/sources.list.d/oneiric.list -O /etc/apt/sources.list.d/medibuntu.list[/PHP]
could be the root of the problem. *I.E.* did you change _oneiric_ to _lucid_?

---

### Post by snowpine on 2012-02-26
I am confused because you said you installed Ubuntu 10.04, yet the link you provided is specific to 11.10. You need to use documentation that is specific to your chosen Ubuntu release.

The typical method for installing GIMP in any Ubuntu release is:

```
sudo apt-get update
sudo apt-get install gimp
```

Be careful using 3rd-party documentation; the most reliable how-to's and tutorials can be found at ubuntu.com.

---

### Post by haunted house on 2012-02-26
Yes I used the third party page to do following steps on the page.


7, 7a), 7c


About Ubuntu still says 10.04 by the way.

So how do I unconfuse the Ubuntu installation?

---

### Post by snowpine on 2012-02-26
> **haunted house said:**
> Yes I used the third party page to do following steps on the page.


7, 7a), 7c


About Ubuntu still says 10.04 by the way.

So how do I unconfuse the Ubuntu installation?

I can't support you with some random guy's blog, sorry, you would have to ask the author. :)

Did the instructions in my previous post help you install GIMP?

---

### Post by haunted house on 2012-02-26
> **snowpine said:**
> I am confused because you said you installed Ubuntu 10.04, yet the link you provided is specific to 11.10. You need to use documentation that is specific to your chosen Ubuntu release.

The typical method for installing GIMP in any Ubuntu release is:

```
sudo apt-get update
sudo apt-get install gimp
```Be careful using 3rd-party documentation; the most reliable how-to's and tutorials can be found at ubuntu.com.
I just copied and pasted 

sudo wget [http://www.medibuntu.org/sources.list.d/oneiric.list](http://www.medibuntu.org/sources.list.d/oneiric.list) -O /etc/apt/sources.list.d/medibuntu.list

i.e did not change oneiric

---

### Post by haunted house on 2012-02-26
> **snowpine said:**
> I can't support you with some random guy's blog, sorry, you would have to ask the author. :)

Did the instructions in my previous post help you install GIMP?

I did that

and I got 

dpkg: configuration error: /etc/dpkg/dpkg.cfg.d/multiarc:1: unknown option 'foreign-architecture'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by snowpine on 2012-02-26
(sorry, cross-post)

Personally I would fresh reinstall and in the future use:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

And be sure to follow the documentation for your specific release.

Perhaps the author of that blog, or another poster here, can help repair the damage to your current system, without a reinstall. :)

---

### Post by haunted house on 2012-02-26
Yes it may well be easier to do that - that is what I was totally thinking - total reinstall - as I have only just installed it anyway.

Anyway my graphics card cannot cope with Unity - but I prefer KDE desktop, so would you recommend to stick with 10.04?

---

### Post by snowpine on 2012-02-26
> **haunted house said:**
> Yes it may well be easier to do that - that is what I was totally thinking - total reinstall - as I have only just installed it anyway.

Anyway my graphics card cannot cope with Unity - but I prefer KDE desktop, so would you recommend to stick with 10.04?

I am not an Ubuntu user, so I'm not the best person to ask. The general advice is 10.04 if you prefer software from April 2010, 11.10 if you prefer software from Oct. 2011, and 12.04 if you want a preview of the upcoming April 2012 release.

---

### Post by sidzen on 2012-02-26
Go to a search page like [https://startpage.com](https://startpage.com) and type in "xubuntu mirror" and choose something like [*here*]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/") then I recommend going with the Alternate Install ISO, as it allows more options on the install; plus the page gives all sorts of instructions like how to burn an iso install CD, and more.  

Once you get it installed, search on "techie moe's package management tutorial"

Best wishes!

---

