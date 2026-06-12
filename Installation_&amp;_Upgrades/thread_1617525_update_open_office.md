---
title: "update open office"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by c2tarun on 2010-11-09
how can i update my open office??

---

### Post by snowpine on 2010-11-09
You can use the Ubuntu Update Manager, or if you prefer the command line:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by TBABill on 2010-11-09
What version of OpenOffice do you have? What are you trying to update to? Which version of Ubuntu are you currently running? All those factors determine what you can do within the repositories of your current version, but you can also download from OpenOffice to have the latest (not the preferred method, however). But downloading outside the repo is not the same as upgrading your version to a newer one via the update/upgrade process mentioned above.

---

### Post by Hagar Delest on 2010-11-09
Personally, I always install the latest vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by c2tarun on 2010-11-10
> **snowpine said:**
> You can use the Ubuntu Update Manager, or if you prefer the command line:

```
sudo apt-get update
sudo apt-get upgrade
```

i tried these but then i found there are no office link in my repository
i added :
  ```

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) lucid main 
```

the above two line in /etc/apt/sources.list file
but also it is not upgrading.
i looked at the website and found there is 3.2.1 version available
but mine is still 3.2.0

??
i m using lucid

---

### Post by snowpine on 2010-11-10
3.2.0 is the correct version for Lucid according to: 
[http://packages.ubuntu.com/lucid/openoffice.org](http://packages.ubuntu.com/lucid/openoffice.org)

---

### Post by tgaston34 on 2010-12-06
Ok I need some help on this same subject I am still new to Ubuntu and was totally hatting 10.04 all the hip was pure crap in my mind, I was on a stable 9.04 Ubuntu when I upgrade worse mistake of my life crashed my system and could get nothing to work had to format HD and start over to find out I couldn't get windows back whole other story, I just loaded Ubuntu 10.10 and seems to be working fine but know I am wanting to install latest OpenOffice program and I need to know how? I tried the advice gave here and it didn't work can somebody tell me what I am doing wrong Thanks Tony

---

### Post by Hagar Delest on 2010-12-06
See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Works fine on xubuntu 10.10.

---

### Post by c2tarun on 2010-12-06
> **tgaston34 said:**
> Ok I need some help on this same subject I am still new to Ubuntu and was totally hatting 10.04 all the hip was pure crap in my mind, I was on a stable 9.04 Ubuntu when I upgrade worse mistake of my life crashed my system and could get nothing to work had to format HD and start over to find out I couldn't get windows back whole other story, I just loaded Ubuntu 10.10 and seems to be working fine but know I am wanting to install latest OpenOffice program and I need to know how? I tried the advice gave here and it didn't work can somebody tell me what I am doing wrong Thanks Tony


upgrading to newer version from the older one always involves some risk. but after all its open source code and we are the one who will solve the errors and make each version better and better. just have some patience and keep reporting bugs. most of the critical bugs are being solved at launchpad. you can also refer there.

---

### Post by IndyGunFreak on 2010-12-06
> **c2tarun said:**
> upgrading to newer version from the older one always involves some risk. but after all its open source code and we are the one who will solve the errors and make each version better and better. just have some patience and keep reporting bugs. most of the critical bugs are being solved at launchpad. you can also refer there.

Indeed... thats one reason I never "upgrade" and simply backup and reinstall.  I never "upgraded" a Redmond OS either.

I am curious though, did he upgrade from 9.04-10.04, by skipping 9.10?  If so, it's hard to blame the OS, because he didn't follow the upgrade instructions.

---

### Post by tgaston34 on 2010-12-07
Thanks for your help on office. to answer the question though about my upgrades I went to 9.10 then done the updates like normal and then when it was time I upgraded to 10.04 but you make a valid point don't upgrade install fresh and backup the system thanks for the advice

---

