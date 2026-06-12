---
title: "Do-release-upgrade with the aptitude equivalent of --without-recommends?"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by Rexilion on 2013-11-10
Hello everyone,

This is the first time I upgraded an installation without a full reïnstall. It was quite convenient, actually.

Only large downside is the fact that do-release-upgrade has no '--without-recommends' switch like aptitude. I install Ubuntu like this:
- installation with cli.seed (bare bone commandline installation)
- aptitude -R <huge package list containing only packages that I need>

This results (in our case) in a pretty slim 3 Gigabyte XFCE installation capable of powering our main desktop. This desktop serves the printer (Airprint, Samba, CUPS HTTP). Collects e-mail. Handles a public share and is capable of media playback. Which is quite nice for 3 Gigabytes.

However, after the succesful upgrade to 13.10, the installation grew to 4,6 Gigabytes.

I was wondering, is it possible to upgrade without installing all the packages mentioned in the Recommends field of each package?

If not, I will try to upgrade the next time by adjusting /etc/apt/sources.list to the new distribution and start upgrading. Is that a viable alternative?

                      Thanks

---

### Post by Rexilion on 2013-11-15
* polite bump * (anyone?)

---

### Post by Frogs Hair on 2013-11-15
As you may already know there is no install recommends command for individual packages or groups or packages , but  I have never read about applying this to an entire distribution upgrade or what the outcome would be. The command may require a list of  specific package names.   
```
--no-install-recommends 
``` 
See: 
```
man apt-get
```
In the future  To generate a list of installed packages/software in a text file create a folder in the home directory named install and run the following command.  
```

dpkg --get-selections > ~/install/installed-software

```

---

### Post by Rexilion on 2013-11-15
Yes, I will try that. And then just replace all instances of the current distro with the name of current distro + 1 in /etc/apt/sources.list{.d}. And see what happens!

(and of course, temporarily disable all other repo's)

---

