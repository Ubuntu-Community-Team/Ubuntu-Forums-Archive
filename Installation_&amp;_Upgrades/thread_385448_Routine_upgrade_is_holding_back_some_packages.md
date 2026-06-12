---
title: "Routine upgrade is holding back some packages"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Levander on 2007-03-15
I'm running "sudo aptitude upgrade" on my Dapper box for the first time in a long time and it's saying it's going to hold back linux-headers-generic, linux-image-generic, and linux-restricted-modules-generic, but I'm not sure why.  I'm guessing it has something to do with when I installed the nvidia hardware accelerated drivers from the repository awhile back?

Output from "sudo aptitude update":

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-generic 
The following packages have been kept back:
  linux-headers-generic 
The following packages will be upgraded:
  ekiga firefox firefox-gnome-support gnupg imagemagick libmagick9 libnspr4 libnss3 libpq4 libxine1 
  linux-libc-dev linux-restricted-modules-common linux-source-2.6.17 lvm2 mozilla-firefox 
  mozilla-thunderbird nvidia-glx slocate tcpdump tzdata ubuntu-docs update-manager 
22 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 90.0MB of archives. After unpacking 471kB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

---

### Post by Arby on 2007-03-16
Those packages are being held back because the dependencies have changed and aptitude doesn't know how to resolve them. Chances are they depend on something you don't yet have installed. There's a good article here [http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69) that explains what's going on and how to fix it. With a bit of luck running ```
sudo aptitude dist-upgrade
``` should sort you out. But please read the article first to see why.

Hope that helps.
Arby

---

### Post by halw on 2007-03-16
> **Arby said:**
> Those packages are being held back because the dependencies have changed and aptitude doesn't know how to resolve them. Chances are they depend on something you don't yet have installed. There's a good article here [http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69) that explains what's going on and how to fix it. With a bit of luck running ```
sudo aptitude dist-upgrade
``` should sort you out. But please read the article first to see why.

Hope that helps.
Arby

Nice catch. Very informative.

---

### Post by Arby on 2007-03-16
Thanks. 

the same thing happened to me a few weeks back. Google was my friend. That debianadministration site is generally worth a read, there's often good stuff there.

---

### Post by Levander on 2007-03-17
Okay, so I'm still trying to figure out what's going on.  The output from running "sudo aptitude dist-upgrade" is below.

Is it just simply because they upgrade edgy from kernel 2.6.17-10 to 2.6.7-11 that I have to dist-upgrade, instead of just a regular upgrade?  Why would Ubuntu upgrading the kernel version require me to do a dist-upgrade instead of just a regular upgrade?

```

levander@louis:~ $ sudo aptitude dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  linux-headers-2.6.17-11 linux-headers-2.6.17-11-generic linux-image-2.6.17-11-generic 
  linux-restricted-modules-2.6.17-11-generic 
The following NEW packages will be installed:
  linux-headers-2.6.17-11 linux-headers-2.6.17-11-generic linux-image-2.6.17-11-generic 
  linux-restricted-modules-2.6.17-11-generic 
The following packages will be upgraded:
  ekiga firefox firefox-gnome-support gnupg imagemagick libmagick9 libnspr4 libnss3 libpq4 libxine1 
  linux-headers-generic linux-image-generic linux-libc-dev linux-restricted-modules-common 
  linux-restricted-modules-generic linux-source-2.6.17 lvm2 mozilla-firefox mozilla-thunderbird 
  nvidia-glx slocate tcpdump tzdata ubuntu-docs update-manager 
25 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 129MB of archives. After unpacking 174MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

---

### Post by Kateikyoushi on 2007-03-17
Because you might use external modules which are not in main repository drivers like nvidia which can break with the kernel upgrade.

---

### Post by Levander on 2007-03-17
Okay, now we are getting somewhere.  I thought it had to do with me installing those nvidia drivers.

So yes, I have the nvidia driver installed.  1.) Is there anyway of knowing if the nvidia driver is going to break because of the kernel upgrade, before I actually perform the kernel upgrade?

2.) If we know it won't break nvidia, why does Ubuntu make me dist-upgrade at all here? And, 

3.) if I hadn't installed the nvidia driver, would I still need to do a dist-upgrade when a kernel version is released?  I just don't remember having to do that before I installed the nvidia driver.

---

### Post by Kateikyoushi on 2007-03-18
As far as I know you have to reinstall the nvidia driver for the new kernel.
I always go with dist upgrade, do not even bother with upgrade, but I do not use any external modules either. What;s the difference ?

>     * apt-get dist-upgrade: 

    the command upgrades packages trying to satisfy the dependencies in a "smart" way -- that usually means removing packages. It is not recommended to use it if you don't know exactly what you are doing. 

    * apt-get upgrade: 

    the command upgrades only the upgradable packages, it doesn't remove packages. From man apt-get: "New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version." 

---

### Post by Levander on 2007-03-18
> **Kateikyoushi said:**
> As far as I know you have to reinstall the nvidia driver for the new kernel.
I always go with dist upgrade, do not even bother with upgrade, but I do not use any external modules either. What;s the difference ?

The difference is that I'd just like to know how this stuff works.  Those three questions above are what I don't understand.

---

