---
title: "Upgrade and Installation without Internet"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by srikrishnan on 2010-07-11
Hi all,

I have no internet connection in my home. I have installed Ubuntu 10.04 LTS through CD in my system. Now I want to make updates and new software installations in my system. Is it possible by getting the updates and softwares from other system through pen drive and install it in my home system?

I am a very beginner to Linux. Can anybody help me by explaining the procedure in detail?

Thanks in Advance,
Srikrishnan

---

### Post by labinnsw on 2010-07-12
> **srikrishnan said:**
> Now I want to make updates and new software installations in my system. Is it possible by getting the updates and softwares from other system through pen drive and install it in my home system?

Yes. Keep your installation CD handy in case of dependencies and get .deb packages. They are the easiest for the new comer.

---

### Post by srikrishnan on 2010-07-14
Hi,

Thanks for your reply,

But I am not able to understand what you are said in your mail. Can you explain some more in detail?

Thanks,
Srikrishnan

---

### Post by labinnsw on 2010-07-14
Say for example you want to install Skype.
A.1.Search for skype (at [www.google.com](www.google.com))
A.2. Follow the resultant links to the package.
(in this case download >> download Skype >> Download Now >> Ubuntu 8.10+ 32-bit or Ubuntu 8.10+ 64-bit)
The file should have a name ending in .deb (just like Windows packages end with .exe) the current Skype package is skype-ubuntu-intrepid_2.1.0.81-1_i386 for a 32-bit system.
A.3. Save the package to your portable storage medium.
A.4. Once on your system, to install the file double click on it.

If there are any unsatisfied prerequisites, you will get an error message indicating what is required. These can usually be found on the installation CD and will also end with .deb. 
B.1 Using nautilus (the gnome file browser), search the installation disc.
B.2. Double click to install these packages also.

---

### Post by srikrishnan on 2010-07-16
Hi,

Thanks for your reply regarding install new softwares.

Can you explain How I can make OS updates, what is the procedure for that?

Thanks,
Srikrishnan

---

### Post by TalSar on 2010-07-16
There are two ways:

you can open a terminal and type
```
sudo apt-get update
sudo apt-get upgrade
```

Or you go in your menu: system => settings => updates

---

### Post by mörgæs on 2010-07-16
True, but these commands need internet access. 

Best is, if you from time to time could bring your computer to a place with internet and run these commands (and install new applications, as needed). 

You could also add

```
sudo apt-get clean
```to the procedure.

---

### Post by robert shearer on 2010-07-16
Use Keryx..

[http://keryxproject.org/](http://keryxproject.org/)

> Keryx is a portable, cross-platform package manager for APT-based (Ubuntu, Debian) systems. It provides a graphical interface for gathering updates, packages, and dependencies for offline computers. Keryx is free and open source. 

Means that **it** takes care of the dependencies and you can run it from other platforms.
So if you can only access the Internet from say a public library or internet cafe that is using Windows then you can still get the Ubuntu packages you need.

---

### Post by TalSar on 2010-07-16
> **mörgæs said:**
> True, but these commands need internet access. 


Can't you use a CD as repository? I thought that's possible.

---

### Post by mörgæs on 2010-07-16
Yes, one can use it, but it will not give any results, since the CD is not updated. 

The 9.10 install CD is unchanged throughout the life time, and 10.04 will only be updated four times in its five years.

I have not heard of Keryx before, but it sounds like a solution.

---

### Post by labinnsw on 2010-07-16
> **mörgæs said:**
> True, but these commands need internet access.
The commands should actually be
```
sudo apt-dcrom add
sudo apt-get update
```

Not recommended for OS upgrade.
These add the cd to the repositories and updates the system using the cd as the repository. You will not have access to updates beyond the release date of that particular cd.

---

### Post by labinnsw on 2010-07-16
Deleted

---

### Post by labinnsw on 2010-07-16
Deleted

---

