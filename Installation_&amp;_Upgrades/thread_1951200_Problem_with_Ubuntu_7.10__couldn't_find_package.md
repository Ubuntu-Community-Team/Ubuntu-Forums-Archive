---
title: "Problem with Ubuntu 7.10:  couldn't find package"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by RadonZR on 2012-04-02
Hi, i am a newbie with Ubuntu und need for helps.
i have to use the old version of Ubuntu 7.10 for my work and can not do anything with it.
1. i can install any thing of the packages (with   or without Internet)
sudo apt-get install ***
Reading package list... Done
Building dependency tree
Reading state information...Done
E: Couldn't find package ***
(i did try some of the package such as build-essential, sysstat etc.)
2. sudo apt-get update does not work either.
3. Ubuntu System could not mount any of my extern devices (hard disk oder usb stick)

please help

many thanks in advance

---

### Post by coffeecat on 2012-04-02
Welcome to the forum.

Support for 7.10 ended in April 2009, three years ago. There have been no updates or security patches for that release since then. The repositories are closed.

> **RadonZR said:**
> i have to use the old version of Ubuntu 7.10 for my work and can not do anything with it.

Why do you have to use an obsolete version? Is there any reason why you cannot install a supported version?

There is an old-releases repository from which you can get updates and applications for 7.10, but they will be obsolete ones. I would not recommend this because running such an old version is a security risk if you connect to the internet.

---

### Post by RadonZR on 2012-04-02
Hi, thank you for the post.
that means i can not do anything to fix the error, when the repositories are closed?
i have to use this Version for some hardware performance tests. Ubuntu Gutsy must be installed on my laptop and ran the test for comparation with the embedded system that we have on the tester, which is similar to Ubuntu Gutsy.

---

### Post by coffeecat on 2012-04-02
If you really need to run 7.10/Gutsy, then you can change your repositories as described here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The page is for end-of-life upgrades which doesn't seem to be relevant to your situation, but you'll find the changes you need to make to /etc/apt/sources.list under the heading "Requirements" on that page. Substitute "gutsy" for "CODENAME" and it should then work for you.

To edit the /etc/apt/sources.list file, you need to open a terminal in Gutsy and use this command:

```
gksudo gedit /etc/apt/sources.list
```

Post back if you need any help with this.

---

### Post by RadonZR on 2012-04-02
thanks a lot, i would prefer not to update to LTS 8.04

i actually read the link for repositeries before

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
or 
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

and did do what needed to do but it did not work out. i still have the error message (i did connect to the internet): "The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

well, what should i do now?
thanks.

---

### Post by Topsiho on 2012-04-02
I found this website:

[http://old-releases.ubuntu.com/releases/7.10/](http://old-releases.ubuntu.com/releases/7.10/)

but did not try it.

Using an old and unsupported distro version is really unsafe when connected to the internet.

Topsiho

---

### Post by coffeecat on 2012-04-02
> **RadonZR said:**
> thanks a lot, i would prefer not to update to LTS 8.04

I wasn't suggesting you do. The link simply tells you what changes you need to make to /etc/apt/sources.list. That's the only part relevant to your situation.

> **RadonZR said:**
> 
well, what should i do now?
thanks.

If you did not run "sudo apt-get update" run it now. Do you get an error message? Please post the contents of your edited /etc/apt/sources.list file.

> **Topsiho said:**
> I found this website:

[http://old-releases.ubuntu.com/releases/7.10/](http://old-releases.ubuntu.com/releases/7.10/)

The OP is trying to update and install new software to a Gutsy/7.10 installation, not download the 7.10 ISO.

---

### Post by RadonZR on 2012-04-03
hi, i am at work now and can not write much.
1. I think some problems will be solved when i get can get access to my USB Driver. But the System can mount my USB or any of the external USB Hard Drive. 
2. yes, i did do apt-get update and apt-get install but it did not work. --> couldn't find the package xyz. I tried the update with Software Sources too, but it can connect and dowload to universe and multiverse. i did actived all the option in sources.list

many thanks.

---

