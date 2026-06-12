---
title: "Is this possible?"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by jmedina on 2007-11-25
I have heard you can run Ubuntu or Opensuse in Windows XP. Is this true? What would I need?

---

### Post by LaRoza on 2007-11-25
VirtuaBox (among others) [http://www.virtualbox.org/](http://www.virtualbox.org/)

It handles many Operating Systems, including Ubuntu. It can handle other Windows, Linux, BSD, DOS, and others.

---

### Post by sirdilznik on 2007-11-25
I'm not sure about Ubunto or OpenSuse, but I know there are minimalist type distros that can run from within another operating system (Windows included).  [Damn Small Linux](http://damnsmalllinux.org/) comes to mind off the top of my head, but there are others I'm sure.

---

### Post by jmedina on 2007-11-25
Cool! Has anybody tried it before? Does it take up a lot of RAM and Space?

---

### Post by jocko on 2007-11-26
> **jmedina said:**
> I have heard you can run Ubuntu or Opensuse in Windows XP. Is this true? What would I need?

> **jmedina said:**
> Cool! Has anybody tried it before? Does it take up a lot of RAM and Space?

VIrtualbox should be fine. I use it to run windows from within ubuntu, but it should work the other way around.
You will need to have enough harddrive space to make a virtual harddrive for each operative system you want to run. I think 8 Gb per virtual disk should be a good size (but make sure you still have free space on your actual harddrive).

The more RAM you can give your virtual machine the better for the virtual OS, but this means windows will be able to use less RAM when the virtual machine is running.
I have 1.5 Gb RAM and give 768 Mb to the virtual machine, which leaves more than enough to run both OS's.
If you have less RAM you should make sure your main OS gets to keep enough RAM to run smoothly (In my experience, WIndows XP runs poorly on less than 512 Mb, almost unbearably slow on 256 Mb).
Other than that, you will need an image of an install CD for the OS you want to install within the virtual machine. Also, I think the virtualbox webpage will help you with some things and for installing Ubuntu, these forums may be helpful.

---

