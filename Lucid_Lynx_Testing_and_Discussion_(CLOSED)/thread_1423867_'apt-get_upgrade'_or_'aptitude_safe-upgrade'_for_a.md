---
title: "'apt-get upgrade' or 'aptitude safe-upgrade' for alphas?"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2010-03-07
When testing development releases I normally avoid the graphical tools and in a terminal run "sudo aptitude safe-upgrade" after updating package lists...

I read somewhere that you could/should instead use "sudo apt-get upgrade" and avoid "sudo apt-get dist-upgrade"...

My question is, which is better/safer? The aptitude or the apt-get command?

(apologies if this is a silly questions and/or already posted and answered)

---

### Post by zika on 2010-03-07
[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

### Post by 23meg on 2010-03-07
The only relevant difference is that "aptitude safe-upgrade" will install new packages to satisfy dependencies (you can override that with --no-new-installs), whereas "apt-get upgrade" will not. Both are generally safe to use, but since there will occasionally be new packages introduced in the development branch, you might miss them if you only ever use "apt-get ugprade".

However, I would discourage general use of aptitude outside safe-upgrade in the development branch, since it may try to be overly smart and suggest solutions that are unfit, especially when the archive is inconsistent. The general rule with any package manager applies: don't just hit "Y"; read the solution it's suggesting, check what it wants to install, upgrade or remove, and decide accordingly.

If when using "apt-get upgrade", a package is held back for a long time due to a new dependency, try "apt-get install"ing it, and if the problem persists, check the changelog to see what's going on.

---

### Post by VMC on 2010-03-07
I read up on this a long while ago and decided on using aptitude.

Here's some current [links]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=aptitude+or+apt-get") on the subject. And as it states, "The Debian team officially recommends using Aptitude".

If you do use aptitude make sure to use the "-q" option for right now until a fix is issued. I haven't had any issues sense turning off progress report:

```
sudo aptitude -q update && sudo aptitude -q safe-upgrade
```

---

### Post by vishalrao on 2010-03-07
thanks all. i thought aptitude might be better. this sort of reinforces my opinion :)

---

### Post by Atermoon on 2010-03-07
I always use aptitude safe-upgrade. And if a package is held aptitude install <package> to see what will happen, which usually returns a huge list of stuff to be removed so I end canceling it.

---

