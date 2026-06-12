---
title: "In-place / bootstrap install"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by coolaj86 on 2008-07-28
I'm looking for tips to convert from Debian to Ubuntu in-place as cleanly as possible.

WHAT I NEED TO KNOW:
[LIST]
[*]What is the base system meta-package (or list of packages)?
[*]In what order should I install (meta-)packages?
[/LIST]

I've had a lot of trouble with CDs and my clamshell iBook. I've tried burning Ubuntu CDs several times, but to no avail. Luckily a friend of mine happened to have a Debian Lenny net-install cd that worked.

Here's what I've done so far:

I've changed /etc/apt/sources.list to use the Ubuntu PPC repos.
[http://www.debianadmin.com/adding-ubuntu-repositories.html](http://www.debianadmin.com/adding-ubuntu-repositories.html)

```

# Main
deb http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates main restricted

# Universe
deb http://ports.ubuntu.com/ubuntu-ports/ hardy universe
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates universe

# Multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse

# Backports
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-backports main restricted universe multiverse

# Partner
deb http://archive.canonical.com/ubuntu hardy partner

## INCORRECT FOR PPC ##
# Security
#deb http://security.ubuntu.com/ubuntu hardy-security main restricted
#deb http://security.ubuntu.com/ubuntu hardy-security universe
#deb http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Now I want to start installing Ubuntu.
There are likely to be a lot of problems.
If you need to find out which file belongs to a package try:
dpkg --search /path/to/file

```

gpg --keyserver pgp.mit.edu --recv-keys 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
sudo apt-get update
sudo apt-get --yes upgrade
sudo apt-get --yes -d dist-upgrade

#### BE CAREFUL HERE ### DO NOT REBOOT without sysvinit-utils installed
sudo apt-get remove sysvinit-utils
# You'll have to enter "Yes, do as I say!" to continue
sudo apt-get --yes dist-upgrade

sudo apt-get --yes install -d ubuntu-minimal
sudo apt-get remove util-linux                         # Enter "Yes, do as I say!" to continue
sudo apt-get install util-linux util-linux-locale
sudo apt-get --yes --reinstall install ubuntu-minimal
sudo apt-get --yes install -d ubuntu-standard
sudo apt-get --yes install -d ubuntu-desktop

```

Then clean up Debian Lenny packages
```

sudo apt-get autoremove
# more stuff to come

```

---

### Post by theaceoffire on 2008-07-28
I am not a pro or anything, but I got some ideas...


Could you show the output when you type the following:
```
sudo apt-get update
sudo apt-get install [[COLOR="DarkSlateBlue"]ubuntu-desktop[/COLOR]]("apt://ubuntu-desktop")
```


Also, you might try installing xubuntu or kubuntu as a mid-way step...
```
sudo apt-get install [[COLOR="DarkSlateBlue"]xubuntu-desktop[/COLOR]]("apt://xubuntu-desktop") [[COLOR="DarkSlateBlue"]kubuntu-desktop[/COLOR]]("apt://kubuntu-desktop") 
```


The desktop package (If I understand it right) has all the stuff you need... assuming you have apt-get, the kernel, etc...

^_^ Hope this helps... also, maybe something [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=213278") or [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Installation") might be useful?

---

### Post by coolaj86 on 2008-07-28
Darn good thread you referenced:
[http://ubuntuforums.org/showthread.php?t=213278](http://ubuntuforums.org/showthread.php?t=213278)

Things seem to be working ATM (still downloading and installing). It may just have been that that I didn't do a distribution upgrade before trying to install the desktop.
```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

UPDATE:
The fewer packages installed in the Debian system the better. I'm having a heck of a time manually fixing these dependency problems.

---

### Post by coolaj86 on 2008-08-09
So it seems as if the thing to do is to have someone with a clean install get a list of all of the packages installed like so:

```
dpkg --get-selections > ubuntu-VERSION-packages
```

Then get a copy of that file and run

```
apt-get install --yes --reinstall dselect aptitude
aptitude update
dpkg --set-selections < ubuntu-VERSION-packages
dselect
# then select "Install"

```

You'll have to manually resolve some conflicts in a similar pattern to what I did in my first post, but it should work okay.

---

