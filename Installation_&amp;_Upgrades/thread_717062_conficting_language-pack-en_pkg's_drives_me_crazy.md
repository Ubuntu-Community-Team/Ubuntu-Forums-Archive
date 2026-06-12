---
title: "conficting language-pack-en pkg's drives me crazy"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by piotrv on 2008-03-06
I cannot get a conflict between packages solved , which was caused by a freeze of my notebook during a distribution upgrade process. I had to cold reboot the machine.
 After that I tried again:

```

> sudo apt-get upgrade

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  language-pack-en: Depends: language-pack-en-base but it is not installed
E: Unmet dependencies. Try using -f.

```

then

```

> sudo apt-get -f install language-pack-en-base

The following extra packages will be installed:
  language-pack-en
Recommended packages:
  language-support-en
The following NEW packages will be installed:
  language-pack-en-base
The following packages will be upgraded:
  language-pack-en
1 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/3568kB of archives.
After unpacking 11.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing language-pack-en (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 language-pack-en
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I checked with

```

> dpkg-query -W language-pack-en

language-pack-en        1:7.10+20071120

> dpkg -l | grep language-pack | awk '{print $2 $3}'

language-pack-en1:7.10+20071120
language-pack-gnome-en1:7.10+20071120
language-pack-gnome-en-base1:7.10+20071012

> dpkg-query -W language-pack-en-base

language-pack-en-base

> sudo dpkg -C

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 language-pack-en     translation updates for language English

```

then I tried to remove language-pack-en

```

> sudo dpkg -r language-pack-en

dpkg: error processing language-pack-en (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 language-pack-en

```

I cannot instal*l language-pack-en-base* and I cannot remove *language-pack-en* because *language-pack-en-base *seems not to be installed. How can I solve this 'circular' problem?

Did I overlook something?

---

### Post by zvacet on 2008-03-07
```
sudo apt-get install --reinstall language-pack-en
```

---

### Post by piotrv on 2008-03-07
> **zvacet said:**
> ```
sudo apt-get install --reinstall language-pack-en
```

doesn't work either as resulting in (circular)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  language-pack-en: Depends: language-pack-en-base but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by zvacet on 2008-03-07
```
sudo apt-get install language-pack-en-base language-pack-en
```

---

### Post by piotrv on 2008-03-07
> **zvacet said:**
> ```
sudo apt-get install language-pack-en-base language-pack-en
```

results in (with or without* -f* flag):

```
dpkg: error processing language-pack-en (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 language-pack-en
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



I even changed locales back to default en_US ISO-8859-1 from en _AU.UTF-8 as I believed this also might have some miraculous effect. It did not  ;-)

It just doesn't make sense to me how to approach this problem without getting into circular results

---

### Post by piotrv on 2008-03-07
> **zvacet said:**
> ```
sudo apt-get install language-pack-en-base language-pack-en
```

as a last resort I just used brute force:

```
sudo dpkg --force-all -r language-pack-en
```

this did the job ! :-)

and then using the package install sequence as you suggested:

```

sudo apt-get  install language-pack-en-base language-pack-en
```

PROBLEM SOLVED !

---

### Post by zvacet on 2008-03-07
:wink:

---

