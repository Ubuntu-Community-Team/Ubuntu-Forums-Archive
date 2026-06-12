---
title: "dpkg remove and don't work"
date: 2013-09-11
forum: Installation &amp; Upgrades
---

### Post by mj125 on 2013-09-11
I try to upgrade ubuntu and some packge break then  I wrongly do this:


> sudo rm -r /var/lib/dpkg/*


and now I get this:


    > masoud@masoud-PC:~$ sudo apt-get upgrade 
    [sudo] password for masoud: 
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    You might want to run 'apt-get -f install' to correct these.
    The following packages have unmet dependencies:
     ia32-libs : Depends: ia32-libs-multiarch but it is not installable
     wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu5) but it is not installable
    E: Unmet dependencies. Try using -f.


and 
> sudo dpkg --configure -a
    dpkg: error: unable to create new file '/var/lib/dpkg/info/format-new': No such file or directory


and

    > masoud@masoud-PC:~$ sudo apt-get upgrade -f
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Correcting dependencies... failed.
    The following packages have unmet dependencies:
     ia32-libs : Depends: ia32-libs-multiarch but it is not installable
     wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu5) but it is not installable
    E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
    E: Unable to correct dependencies

---

### Post by bkline on 2013-09-11
I'm going to pass on some advice which was given to me a good while ago, when I was dealing with broken upgrades.  I was told that the only reliable way to "upgrade" from one Ubuntu release to the next was not to do it, but instead to back up my data, wipe the system, do a fresh install of the next release, drop the data back in, and re-install any packages I needed.  In spite of the fact that this means some extra steps which I wouldn't have to do in an ideal world, where upgrades did what they're supposed to, the net result is actually much less work and hair-pulling frustration, and much more stable and reliable systems.  I have the extra steps written down so I can almost do the process in my sleep.  Although the advice was presented in a somewhat abrasive way (sort of like "how could you be so naive as to actually trust the upgrade software?"), which put me off at first, I have come to appreciate how valuable the advice was, even if you haven't done something as risky as wiping out the package manager's information, and in your case I think I would follow this advice if I were in your shoes.  Even if you don't, back up your data before blowing away any more pieces of the file system.

Good luck!

---

### Post by ibjsb4 on 2013-09-11
First try

```
sudo apt-get update
```

Then try an upgrade

```
sudo apt-get upgrade
```

---

