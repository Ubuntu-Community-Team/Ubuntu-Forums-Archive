---
title: "Django 1.2"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by sridharpandu on 2009-11-13
I am working on the Django tutorials and need to use the [FONT=Courier, Monospaced]{% csrf_token %}. [/FONT]This works in Django 1.2. The version that ships with Ubuntu 9.10 is 1.1.1. I did a apt-cache search and 1.1.1 seems to be the latest. Does anyone have an idea when Django 1.2 packages would ready so that I can upgrade. (I have found a workaround to include the  [FONT=Courier, Monospaced]{% csrf_token %}[/FONT] token in the current version. But that doesn't seem to be working as intented.

Regards

Sridhar

---

### Post by keywa on 2009-11-14
Same situation here :(

Am wondering should I wait for a package to be released or make my own install to be independent of ubuntu packages?

---

### Post by UncoElite on 2009-11-21
Django 1.2 isn't out yet, the latest stable is 1.1.1
The (default) documentation on their site though is for the development (SVN) version (what is going to be 1.2).

At top of the tutorial pages there is some text that says .... 
> This document is for Django's SVN release, which can be significantly different from previous releases. **Get old docs here: Django 1.0**

the bit that says **Get old docs here: Django 1.0** ... Click that and you'll get the docs that can be used for 1.1.1

Or the link is here...
[http://docs.djangoproject.com/en/1.0/](http://docs.djangoproject.com/en/1.0/)

---

### Post by zepatou on 2010-05-20
Django 1.2 is now out: [http://docs.djangoproject.com/en/dev/releases/1.2/](http://docs.djangoproject.com/en/dev/releases/1.2/)

How do I install it in ubuntu ?
(my version is 9.10 server)

---

### Post by sridharpandu on 2010-05-21
I suggest that you wait for the Ubuntu package. You should check the Ubuntu Package cache to see if Django 1.2 is released. Type the following after you sudo su

apt-cache showpkg python-django

The first line lists the version number. If you find 1.2 the either use the synaptic manager to install it or do an 

apt-get install python-django

If you can't wait for the official Ubuntu release then post the query in the Django forums. Someone there will guide you. 

Best regards

Sridhar

---

### Post by zepatou on 2010-05-21
Yes, I can't wait! ;)

So you suggest a manual install ? I was thinking there might be a backport or something ?

---

### Post by glastonbury on 2010-05-24
I am a relatively new user of Ubuntu and I have similar question about Django 1.2 (and now we're up to 1.2.1). I currently have Django 1.1.1 installed via Synaptic.

-- Generally, how long would it take for 1.2.1 to appear in a package that I can download via Synaptic?

-- If I were to uninstall ver 1.1.1 and manually install ver 1.2.1, would it get installed in the same location that Synaptic installs it?

Thanks for your help.

---

### Post by Drachenfels on 2010-06-25
I found a solution for that. 

First of all

sudo apt-get purge python-django

It should remove django from your system. Next I searched on Django homepage for a newest django. I found a .deb package on Debian website:

[http://packages.debian.org/squeeze/all/python-django/download](http://packages.debian.org/squeeze/all/python-django/download)

Download it. Install it. And you should have django-1.2.1 installed on your machine.

Tested on Karmic Koala. Beware some of my sites have died after upgrading to newest django. ;)

---

### Post by hackeron on 2010-08-08
It is now August and we are still stuck with the outdated 1.1.1 :( - Any official ubuntu packages out there yet?

---

### Post by Ric_ on 2010-08-13
django has been accepted into Maverick 10.10, looks like the 1.2 release was just a little too late to make it into the repositories.

[https://lists.ubuntu.com/archives/maverick-changes/2010-May/000547.html](https://lists.ubuntu.com/archives/maverick-changes/2010-May/000547.html)

---

### Post by radious on 2010-08-31
You can use [pypi]("http://pypi.python.org/") repository to install newest version of Django. For example, if you're using pip (you can also choose easy_install) just type: ```
sudo pip install Django
```.

---

