---
title: "Problem upgrading ubuntu from dapper to edgy"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by cikson on 2007-08-04
I have problem when I am trying to upgrade from 6.06 to 6.10 (from cd).
After typing ```
sudo gksu "sh /cdrom/cdromupgrade"
``` 
I got message:
```
 
[SIZE="4"]**Your system is up-to-date**[/SIZE]

There are no upgrades available for your system. 
The upgrade will now be canceled.

``` :(

But when I type:

```
cat /etc/issue
```

I got this:

```
Ubuntu 6.06 LTS \n \l
``` :(

How to fix this? :confused:

btw: I have 56k  Dial Up Internet connection so I can't upgrade via Update Manager

Thank you

---

### Post by cikson on 2007-08-05
Now instead of first message I have this one:
```
[B]Could not calculate the upgrade
[/B]
A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
```

---

### Post by karlox on 2007-08-05
I also have the same problem, though I'm using the internet and the update-manager.

Thanx to your writing, Igot thisonthe terminal:

@karlox-laptop:/home/karlox# cat /var/log/dist-upgrade/main.logt
2007-08-05 20:36:52,521 ERROR can't import view 'DistUpgradeViewGtk'

I'll investigate it and write down the outcome of it.
If I find it of course!

By the other hand... if anyone knows better, and doesn't mind to tell me a bit whereabout to look at...
... it will be appreciated!! :)

---

### Post by darenw on 2007-08-05
did you try
update-manager -c
(with the -c) ?

---

### Post by karlox on 2007-08-06
So Basically, you want to pass from dapper (6.04) to edgy (6.10)
I think the basic in here are the repositories. It is a txt file located at /etc/apt/sources.list

It is up to this file where to get the information from.
It doesn't matter if it is from a cd, or either the internet.
You just need the repositories that you want to change to (logically)
In this case your repositories are at the moment dapper, and you need the edgy ones.

There is this site where automatically opens you a file txt with the repositories you ask for.
You just need to save it at your home directory, on something like newsources.txt for ex.
go to:  
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
and find out for the repositories you need.

After make a buck up copy of your present sources.list, from the terminal:
cp -v /etc/apt/sources.list ~/oldsources.txt

and then do as root:
cp -v ~/newsources.txt /etc/apt/sources.list
That would change your repositories, just make sure it says edgy, like:
cat /etc/apt/sources.list | less

After all that, you do an update, an upgrade, and a dist-upgrade  with apt-get command. Or aptitude will do it.
Check it out with update-manager too.
If u r still thinking on taking the source from the Cd, just make sure (once again) the repository you choose, has an edgy written on it or something similar!
I'd rather recommend you the use of internet, even if it is with a slow modem, you can leave it over night working, If they charge you per month, 
but if they do by the minute.... Get a better deal!
I hope it works for you!

---

### Post by cikson on 2007-08-06
I have tryed all of the above but the problem is that download would
last 12 hours and ISP charge me per minute:(

This is my sources.list:
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://hr.archive.ubuntu.com/ubuntu edgy main restricted
deb http://hr.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

```

---

### Post by karlox on 2007-08-06
I would put a comment (#) in the three lines for the internet.
Leave uncomment the one from the cd.

I would put a dvd of the distro, because it wil be less limited than the cd, I guess.
And then apt-cdrom or so, to get the new source address from the new dvd.

and then as normal! apt-get update, etc etc...
Check it out, Or get one of these free month-trials from an ISP.

Linux plus internet... comes naturally!!!

---

### Post by cikson on 2007-08-09
Thank you for the help, but I still have the same problem.

---

