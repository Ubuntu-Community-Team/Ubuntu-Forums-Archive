---
title: "how to download .deb files into win7 and install them on ubuntu?"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by ehsango on 2011-05-05
hi friends
where can i download .deb files for ubuntu 10.10 with win7?(cuz i don't have access to the Internet in ubuntu)

---

### Post by Dutch70 on 2011-05-05
You should be able to access the folder that you save them to from Ubuntu, then just cut/paste them in Ubuntu.

When you open your home folder, look on the left side for your computer/windows name.

---

### Post by ehsango on 2011-05-05
i know that
i'm looking for a website to **download** the programs.
deb files of ubuntu programs are really rare!

---

### Post by Dutch70 on 2011-05-05
You can try these 2 sites, other than that, they are all over the web.
[http://linux.softpedia.com/downloadTag/deb]("http://linux.softpedia.com/downloadTag/deb")
[http://www.getdeb.net/welcome/]("http://www.getdeb.net/welcome/")

---

### Post by lykwydchykyn on 2011-05-05
Repositories are just web servers.  The trick is knowing which files you need.

If you need a particular deb, just browse to it in the repository:

[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

There's also apt-offline, a package that allows you to use apt without a network connection (by generating a script that you can run on a computer that does).  I haven't used it, but I found a tutorial for it here:

[http://blog.suroboy.com/offline-package-management-for-apt.htm](http://blog.suroboy.com/offline-package-management-for-apt.htm)

---

### Post by ehsango on 2011-05-06
[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) was exactly what i was looking for
thank you!

---

### Post by ehsango on 2011-05-06
is there any way to know the program's dependencies before switching to ubuntu?

---

### Post by kansasnoob on 2011-05-06
I actually use this:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

It would be helpful to know what package(s) you need to install. I assume something to help sort the networking problem :confused:

But, just for instance, if I wanted the package 'grub-pc' for Maverick I'd click on maverick in that list of distros, and I know grub-pc is in administration utilities. If you don't know what section to look in there's a link to all packages at the bottom of each sub-section.

But back to 'grub-pc':

[http://packages.ubuntu.com/maverick/admin/grub-pc](http://packages.ubuntu.com/maverick/admin/grub-pc)

You can see that it lists the dependencies :)

---

### Post by lykwydchykyn on 2011-05-06
> **ehsango said:**
> is there any way to know the program's dependencies before switching to ubuntu?

That's what a tool like apt-offline does for you; but if you want to do it manually, kansasnoob's suggestion works well.

---

### Post by ehsango on 2011-05-06
that was good but if apt-offline can download the program with all dependencies at once, would you tell me how to use apt-offline with win7?

---

