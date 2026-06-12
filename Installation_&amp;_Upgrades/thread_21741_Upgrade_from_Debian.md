---
title: "Upgrade from Debian"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by Zaha on 2005-03-23
Hello, 

I'm a current Debian Sarge user and planning to upgrade to Ubuntu. Since the distros use similar underlying systems (essentially apt), I've been thinking if I could switch with less than a full reinstallation.

The most obvious and straightforward way to upgrade would be to change sources.list to ubuntu distributions (by the way, I'm in Finland; which server should I use in sources.list?) and do an apt-get dist-upgrade. If anyone knows how this would work (or even better, has tried it), I'd be interested to hear. If dist-upgrade won't work well enough, what should I do instead?

I need to keep my old personal files and, preferably, the most important config files, too. Reconfiguring X server won't be a big deal (since the upgrade would mean changing from XFree to X.org) and I already use Gnome.

---

### Post by brettl on 2005-03-24
I wish you the best of luck, brave soul...

[From the FAQ...](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge)

Can't say if I'd recommend doing this though :) (Your /home is probably on a different partition, why not just install around it?)

---

### Post by banishedknight on 2005-03-24
Just a few days ago I've upgraded my old woody installation + many backports to Ubuntu Warty. It worked without big problems. 
Try to remove uneeded packages first with the purge option before you update.
But make a backup first ;)

---

### Post by az on 2005-03-24
Woody to Ubuntu works.  Sarge does not.

---

### Post by mnml on 2007-10-30
it is possible to upgrade To debian from Ubuntu?

---

### Post by fearpi on 2008-01-28
> **mnml said:**
> it is possible to upgrade To debian from Ubuntu?

I'm wondering the same thing. I'd do it if I could simply switch software repos.

---

### Post by zvacet on 2008-01-28
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

Then update the package list and install sudo if you don't already have it installed: 
# apt-get update 
As a first step to getting all the installed packages in order, you can manually force a reinstall of every package on your system to the specific version available in Ubuntu, but since a typical Debian system has over a thousand packages installed, that can be rather tedious. You can save yourself some time by writing a little script like this: 
#!/bin/sh 
for name in \Qdpkg --get-selections | grep '[[:space:]]install$' \\ 
  | awk '{print $1}'\Q 
do 
   sudo apt-get install --assume-yes ${name}=\Qapt-cache show $name \\ 
     | grep '^Version' | awk '{print $2}'\Q 
done

It's highly likely that some packages you have previously installed from the Debian archives won't "cross-grade" cleanly to the version available in Ubuntu, and you may have to manually uninstall some packages to allow the process to complete. Depending on how your system is set up, you may need to do a lot of poking and prodding to get to the point where: 
$ sudo apt-get update 
$ sudo apt-get dist-upgrade 
            

can execute cleanly. 
Once you have your existing packages converted to the Ubuntu versions, it's time to pull in the core Ubuntu packages: 
$ sudo apt-get install ubuntu-standard ubuntu-desktop 
            

The result won't be perfect, but you should then have a system that is a reasonable approximation of a full Ubuntu install. 

It is from O´Reilly and I never tryed it.Use it on your own risk.

---

### Post by Pandemic187 on 2008-01-28
Not that this solves the problem, but I wouldn't call switching from Debian to Ubuntu an "upgrade." However, sarge is an old version so for that reason it could be considered as such, since Ubuntu will have much newer packages. But saying, "I'm planning on upgrading from Debian to Ubuntu" sounds like saying Ubuntu is better than Debian...which cannot be assumed.

Other than that, I wish you much success...I've never heard of someone doing this kind of install.

---

