---
title: "Installing a program taking like 30 minutes or so"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by Ninja&gt;Master on 2013-08-07
Hi,
I am installing Perl v5.18 on Ubuntu 11.10 (Yes, I know its an old version). Its been like half an hour since the 'make' process and now its on the 'make test' process. It did not finish yet. Why is it taking so much time to install it? And does all programs take such time to install? Why use Linux if its such a pain to install a simple program? On Windows it takes like 5 minutes.

---

### Post by Cheesemill on 2013-08-07
It's taking such a long time because you are compiling the program from source instead of just installing a pre-compiled binary. It would take just as long in Windows to do the same thing.

You should only compile a program from source as a last resort, the preferred way to install applications is to use the Ubuntu repositories either through the Software Centre or by using the apt-get command. This way the application will install in seconds.

Unfortunately because you are using an outdated OS you don't have the opportunity to install software from the repositories (as well as receiving no security updates or bug fixes). If you were using a version of Ubuntu that was still supported you could use the command...
```
sudo apt-get install perl
```
and it would be installed quickly as well as being automatically updated.

I highly reccomend upgrading your system to a version of Ubuntu that is still supported such as 12.04 or 13.04.

---

### Post by Ninja&gt;Master on 2013-08-07
So, would .deb files install the normal fast way?

---

### Post by cortman on 2013-08-07
> **Cheesemill said:**
> 
I highly reccomend upgrading your system to a version of Ubuntu that is still supported such as 12.04 or 13.04.

^ This. Do the 11.10 repositories still exist, even?

---

### Post by Cheesemill on 2013-08-07
> **Ninja>Master said:**
> So, would .deb files install the normal fast way?

Possibly.

The problem with this approach is that as well as having to find and download the .deb file for perl you would also have to find and download the .deb file for each of its dependencies.

Each of these dependencies also have packages that they depend on so you would have to find out what these are before downloading their .deb files. And so on. And so on.....

In short you should upgrade to a supported version of Ubuntu and then install perl directly from the repositories, in the fashion that the OS was designed to do.

As well as not being able to install packages properly you are also leaving your machine wide open to hackers by using an unsupported, unpatched OS.

---

### Post by Ninja&gt;Master on 2013-08-08
I've installed Lubuntu 13.04 and now everything is cool. Can get apps from the store as well as install it fast. Thanks for the help peeps :D.

Cheers!

---

