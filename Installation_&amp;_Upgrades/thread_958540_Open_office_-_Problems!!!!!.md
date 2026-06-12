---
title: "Open office - Problems!!!!!"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by Sugz on 2008-10-25
Ok so today i tried to install the latest version of Open office.
Great.. but. I needed to uninstall the current version. so i did this in terminal via the sudo apt-get method.

And.. It automatically uninstalled Ubuntu-Desktop!!!

And also i couldnt install the new version of open office because of dependency errors.. 

SO i installed the default version of Open office from the Rops (2.2) 

And it looks something like this.. 

[[IMG]http://img65.imageshack.us/img65/7312/screenshot2tt4.png[/IMG]](http://imageshack.us)
[[IMG]http://img65.imageshack.us/img65/screenshot2tt4.png/1/w495.png[/IMG]](http://g.imageshack.us/img65/screenshot2tt4.png/1/)

it looks bad.. 

SO how do i install the latest version (bearing in mind that i am running the repo version) And not break anything. 
I have tried to follow many guides, but they all go on you having at least version 2.3-2.4 installed. 

Many thanks

---

### Post by Sugz on 2008-10-25
Alright, i have it working ... I have installed Open office in parallel with Open office from the Repos. 

Ok ill show the link that i followed - This workds under Gutsy Tried and Tested. 

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

Enjoy!

---

### Post by jespdj on 2008-10-25
> **Sugz said:**
> And.. It automatically uninstalled Ubuntu-Desktop!!!
The package **ubuntu-desktop** is a meta-package, which means that the package itself doesn't contain anything; it only has a whole list of dependencies. The purpose of this is that you can install all the standard programs that you get with Ubuntu in one go by installing the package ubuntu-desktop.

When you uninstall a program that ubuntu-desktop depends on, for example OpenOffice.org 2.4, then ubuntu-desktop will also be automatically uninstalled. But that doesn't mean that all the programs will be uninstalled.

So, uninstalling ubuntu-desktop is not as bad as it sounds.

---

### Post by jespdj on 2008-10-25
I just found the following guide, which allows you to upgrade your OpenOffice 2.4 to 3.0 without uninstalling ubuntu-desktop:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Note, this is for Ubuntu 8.10 (not 8.04).

---

