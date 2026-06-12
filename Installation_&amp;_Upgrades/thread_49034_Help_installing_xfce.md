---
title: "Help installing xfce"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by velayo on 2005-07-14
First, I want to say that I'm IMPRESSED with ubuntu. I have been switching distros for a while now (since mandrake 8) and have never found one that felt like this one.  What I like the most is that it feels like a OS and not like little patches forced to work together.

I have an old PII 266 laptop that works fine with ubuntu (altough a little too slow).  However, I would like to install xfce and use it as my main DE.  I know it will be more responsive that way.  The problem is that the laptop has no network connection.  I would like to know if any of these ideas can be done:

1.  Connect the laptop to my desktop using a usb cable and creating a network that will allow me to use synaptic to install xfce.

2.  If that is not possible I would like to know where can I find a repository that will allow me to download all the deb packages needed (which packages will I need), and what will be the command to use to install from a burned cd.

I will appreciate any suggestions. Thanks!

---

### Post by badrinarayan on 2005-07-14
[list=1]
[*]Look [http://packages.ubuntu.com/hoary/x11/xfce](http://packages.ubuntu.com/hoary/x11/xfce) for dependencies   
[*]Use sudo apt-cache show package-name to see if the package is not already there.   
[*]Download the deb's for the files you don't have.   
[*]Install using sudo dpkg -i package-name 
[/list] 
Good luck!

Regards
Badri

---

### Post by velayo on 2006-02-09
Thanks! Will be trying that during the weekend.  I'll let you know how it turns out.

---

