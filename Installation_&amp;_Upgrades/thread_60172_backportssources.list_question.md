---
title: "backports/sources.list question"
date: 2005-08-26
forum: Installation &amp; Upgrades
---

### Post by buldir on 2005-08-26
If my sources.list is:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
``` 

Why does apt-get get acroread version 5 when a newer version 7 is available via the backport?  I thought apt-get got the newest version regardless of the order of  the repos in your sources.list file.

---

### Post by DJ_Max on 2005-08-26
[QUOTE=buldir]If my sources.list is:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
``` 

Why does apt-get get acroread version 5 when a newer version 7 is available via the backport?  I thought apt-get got the newest version regardless of the order of  the repos in your sources.list file.[/QUOTE]
 This is true if in fact you updated your local sources.
```
sudo apt-get update
```

---

### Post by buldir on 2005-08-26
Yep...I updated after adding the backport.  I will try again later tonight.

---

### Post by Oxygene on 2005-08-26
Hello,

I currently encounter the same problem. Some packages seem to have higher priority over packages from backports. This breaks dependencies in my apt, too.

An example:
there is a newer version of amarok and amarok-xine in backports. the new version of amarok-xine is displayed in synaptic & co. but amarok is still the hoary version and other versions are not listed for this package (that means, I cannot go to Package->Force version).

The same happens for other packages like gimp -> gimp-data.

Firefox packages seem to be even more weird. Trying to opgrade mozilla-firefox would remove mozilla-firefox-gnome-support.
Trying to upgrade mozilla-firefox-gnome-support fails, because it depends on firefox-gnome-support (notice the missing mozilla-prefix)
firefox-gnome-support fails to install because "firefox" is not installable (it is not listed at all)

Whats wrong here???

---

### Post by buldir on 2005-08-26
[QUOTE=Oxygene]Hello,

I currently encounter the same problem. Some packages seem to have higher priority over packages from backports. This breaks dependencies in my apt, too.

An example:
there is a newer version of amarok and amarok-xine in backports. the new version of amarok-xine is displayed in synaptic & co. but amarok is still the hoary version and other versions are not listed for this package (that means, I cannot go to Package->Force version).

The same happens for other packages like gimp -> gimp-data.

Firefox packages seem to be even more weird. Trying to opgrade mozilla-firefox would remove mozilla-firefox-gnome-support.
Trying to upgrade mozilla-firefox-gnome-support fails, because it depends on firefox-gnome-support (notice the missing mozilla-prefix)
firefox-gnome-support fails to install because "firefox" is not installable (it is not listed at all)

Whats wrong here???[/QUOTE]

It sounds like they need to resolve some issues between main and the backports.  Here's the scoop on the [Firefox backport issue](http://ubuntuforums.org/showthread.php?t=51964&highlight=backport+conflicts).

---

### Post by Hobbsee on 2005-08-27
[QUOTE=Oxygene]Hello,

I currently encounter the same problem. Some packages seem to have higher priority over packages from backports. This breaks dependencies in my apt, too.

An example:
there is a newer version of amarok and amarok-xine in backports. the new version of amarok-xine is displayed in synaptic & co. but amarok is still the hoary version and other versions are not listed for this package (that means, I cannot go to Package->Force version).

The same happens for other packages like gimp -> gimp-data.

Firefox packages seem to be even more weird. Trying to opgrade mozilla-firefox would remove mozilla-firefox-gnome-support.
Trying to upgrade mozilla-firefox-gnome-support fails, because it depends on firefox-gnome-support (notice the missing mozilla-prefix)
firefox-gnome-support fails to install because "firefox" is not installable (it is not listed at all)

Whats wrong here???[/QUOTE]

Yay!  I'm not the only person having this trouble...does anyone have a solution to this as yet?

---

### Post by buldir on 2005-08-27
Hobbsee,
If you do a forum search for "backports", you will see there are lots of problems right now.  One thread mentions that if you go to:

[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)

and search around in the hoary-extras and hoary-backports directories you will see packages like acroread 7, newer versions of wine, and Java, but if you include these repos in your /etc/apt/sources.list file and do:

```
sudo apt-get update
``` 
you may get errors when trying to install said packages.  The problem it seems, was that these newer packages were not included, or updated, in "Packages.gz", which is basically an index for the package list.  However, I just checked the contents of "Packages.gz" in the hoary-extras repo and the problem seems to have been fixed.  The file date of "Packages.gz" is 08/27/05.  Rock on jdong!

---

