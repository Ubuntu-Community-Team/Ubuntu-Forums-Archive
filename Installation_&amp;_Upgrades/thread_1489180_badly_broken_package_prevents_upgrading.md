---
title: "badly broken package prevents upgrading"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by bobdobbs on 2010-05-20
Hi guys.

I've badly broken cinellera, and now I can't successfully run 'apt-get dist-upgrade' successfully.

I've been using linux in different forms for about a decade, and whenever the package management breaks, I've had to re-install the OS. I'm wondering if there is a way to actually fix the problem.

At the moment, if I run apt-get dist-upgrade, this happens:

```
After this operation, 171MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 522586 files and directories currently installed.)
Removing cinelerra ...
Description:	Ubuntu 9.10
en_NZ.iso885915
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess installed post-removal script returned error exit status 1
locale "ru_RU.KOI8-R" not in archive
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@faustina:~# 

```

If I try to apt-get or dpkg remove cinellera, I am told that the package can't be removed because it is not installed.

Is there a way to fix broken package management on ubuntu ?

---

### Post by wilee-nilee on 2010-05-20
> **bobdobbs said:**
> Hi guys.

I've badly broken cinellera, and now I can't successfully run 'apt-get dist-upgrade' successfully.

I've been using linux in different forms for about a decade, and whenever the package management breaks, I've had to re-install the OS. I'm wondering if there is a way to actually fix the problem.

At the moment, if I run apt-get dist-upgrade, this happens:

```
After this operation, 171MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 522586 files and directories currently installed.)
Removing cinelerra ...
Description:	Ubuntu 9.10
en_NZ.iso885915
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess installed post-removal script returned error exit status 1
locale "ru_RU.KOI8-R" not in archive
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@faustina:~# 

```

If I try to apt-get or dpkg remove cinellera, I am told that the package can't be removed because it is not installed.

Is there a way to fix broken package management on ubuntu ?

Why are you running in root? go to synaptic and look at broken packages.

---

### Post by bobdobbs on 2010-05-20
> **wilee-nilee said:**
> Why are you running in root? go to synaptic and look at broken packages.

I usually run as root in order to do administrative tasks. 
This is actually quiet normal outside of the ubuntu world, and can make things simpler. 
I don't run as root for tasks that do not require it.

Whenever I run synaptic as a normal user, I get a message saying that I will not be able to make changes to the system.

When I run synaptic as root, and attempt to fix broken packages, I get the error message:
E: cinelerra: subprocess installed post-removal script returned error exit status 1

---

### Post by wilee-nilee on 2010-05-20
> **bobdobbs said:**
> I usually run as root in order to do administrative tasks. 
This is actually quiet normal outside of the ubuntu world, and can make things simpler. 
I don't run as root for tasks that do not require it.

Whenever I run synaptic as a normal user, I get a message saying that I will not be able to make changes to the system.

When I run synaptic as root, and attempt to fix broken packages, I get the error message:
E: cinelerra: subprocess installed post-removal script returned error exit status 1

Have you tried ```
sudo dpkg --configure -a
``` from the terminal not in root. there is another command that I don't remember as well. I think running in root is the root to your problems as far as having to do reinstalls.

Also did you have cinelerra installed and then removed it manually by deleting from the computer rather then a purge or remove via synaptic or the command in the terminal.

---

### Post by bobdobbs on 2010-05-20
> **wilee-nilee said:**
> Have you tried ```
sudo dpkg --configure -a
``` from the terminal not in root. there is another command that I don't remember as well. I think running in root is the root to your problems as far as having to do reinstalls.


dpkg --configure -a does nothing to fix the problem.

I don't see running as root to administer the system can by itself cause problems. 
Only the root user can actually do certain neccessary tasks.
Sure, running as root has risks. But if you don't su, then there are some things that you simple can't do.

> **wilee-nilee said:**
> 
Also did you have cinelerra installed and then removed it manually by deleting from the computer rather then a purge or remove via synaptic or the command in the terminal.

Cinellera has been problematic from the initial point of installation. I attempted to uninstall it using apt and dpkg.

---

### Post by wilee-nilee on 2010-05-20
It seems that your convinced of the way you run your computer so I will not waste my time, good luck.

---

### Post by bobdobbs on 2010-05-20
I'm happy to accept any useful advice, should you actually offer any.

> **wilee-nilee said:**
> It seems that your convinced of the way you run your computer so I will not waste my time, good luck.

---

### Post by wilee-nilee on 2010-05-20
> **bobdobbs said:**
> I'm happy to accept any useful advice, should you actually offer any.

I did **_don't run in root_** anybody knows this it is common knowledge. There arereasons why Linux is set up this way, if you want root access you run sudo, if it can't be done that way then you shouldn't be messing with it, this is why you probably have been having problems in the past and now. Linux is not like other root running systems, other then puppy Linux.

---

### Post by bobdobbs on 2010-05-20
You might have missed my comment above, so I will re-iterate:

I do not run as root for everyday use.

However, there are some administrative tasks that require the user to run as root. 
For example, administering a web server. You can't load and unload modules or restart the server unless you are root. You can't change many networking settings without being root. 

You say that linux is set up so that you must use sudo for root access. This is actually not true. Linux allows users to become root via su, or log in at a terminal as root.

Sudo is relatively new in the linux toolset. I'd bet that many distro's don't even have it installed by default. In the linux world, there is a "sudo way of doing things". This is not neccessarily the only way. And it is certainly not "the one true linux way" of doing things.

I could be wrong, but I suspect that the majority of your experience is on more recent consumer versions of linux, and possible even confined to ubuntu, where the documentation for these distro's is quiet sudo centric.

I very much doubt that you could find any documentation for ubuntu that says that you must not stray from using sudo, and that you should never use su.
But hey, if you can find such reccomendations in the official docs, then feel free to point them out to me. I'll happily admit the error of my ways.

> **wilee-nilee said:**
> I did **_don't run in root_** anybody knows this it is common knowledge. There arereasons why Linux is set up this way, if you want root access you run sudo, if it can't be done that way then you shouldn't be messing with it, this is why you probably have been having problems in the past and now. Linux is not like other root running systems, other then puppy Linux.

---

### Post by wilee-nilee on 2010-05-21
So I would agree that su or gksu is needed and used at times, but in just trying to remove and install regular programs, this can be problematic if you don't know when and where it should be used. You have to realize that your thread started with comments that your computers can never be upgraded but need a fresh install, this is a red flag for me. 

I started out as a open source user and have used over 20 or so distros including arch linux, and only bought W7 about 6 months ago with a student discount, and the computer I use it on started with XP.

Here is a link that some what explains the inherent danger of just making sure a user knows when to run in root and what the definitions are.
[http://www.linfo.org/root.html](http://www.linfo.org/root.html)

I don't doubt that you can come up with any hind-site bias argument, but I think your forgetting that this is hind site information. You never mentioned anything about using a server...etc.

I don't really care what you think my level of experience as my computers are not borked yours are, and with so much apparent knowledge I am just curious as to why you would even need help from a forum. ;)

---

### Post by bobdobbs on 2010-05-21
Congratulations.
You have missed the point with skill and dexterity.

The level of access you need to a *nix system to administer a webserver is the same level you need to add and remove system wide packages.

Using su and then apt-get is pretty much the same as using sudo and apt-get. Using sudo is no garuantee that things will not break.

The advice that you have given (don't be root) is understandable.
But there are always good reasons to be root. If, as you say, you have used linux so much, then you would know. 
If you had read the document that you linked to, you would have noticed that it describes tasks that require the user to be root.
 
In my case, things have broken. Advice on how to do repair would be appreciated.

---

### Post by Soul-Sing on 2010-05-21
```
gksudo nautilus
```

remove via nautilus these package in /var/lib/dpkg/info

- Cinelerra 

after removing this, close nautilus.

```
sudo apt-get update
```

via:
```
gksudo nautilus
```

navigate via nautilus to


/usr/bin/cinelerra

remove it.

close nautilus.

---

### Post by bobdobbs on 2010-05-21
Hi leoquant.

Neither of these files currently exist.

---

### Post by Soul-Sing on 2010-05-21
> **bobdobbs said:**
> Hi leoquant.

Neither of these files currently exist.

bobdogs and: ru_RU.KOI8-R ?
and if you change /var/lib/dpkg/info to /var/lib/dpkg/status?

---

### Post by bobdobbs on 2010-05-21
> **leoquant said:**
> bobdogs and: ru_RU.KOI8-R ?
and if you change /var/lib/dpkg/info to /var/lib/dpkg/status?

```

# ls /var/lib/dpkg/status/
ls: cannot access /var/lib/dpkg/status/: Not a directory

```

Apparently I don't have that dir either.

---

### Post by Soul-Sing on 2010-05-21
close all /apt/dpkg/software centre/synaptic

cd /var/lib/dpkg/info
sudo rm cinelerra.*

last suggestion: ```
sudo dpkg --remove --force-remove-reinstreq cinelerra
```

---

### Post by bobdobbs on 2010-05-21
> **leoquant said:**
> close all /apt/dpkg/software centre/synaptic

cd /var/lib/dpkg/info
sudo rm cinerella.*

last suggestion: ```
sudo dpkg --remove --force-remove-reinstreq cinerella
```

Yeah, I tried this one earlier today too.
It returns:

dpkg: warning: ignoring request to remove cinerella which isn't installed.

It seems that system can't uninstall it, because it doesn't exist. However, when I try and install anything else,

---

### Post by bobdobbs on 2010-05-21
Sorry -  I reread your post and noticed your first direction.

As root, I first backed up the dir /var/lib/dpkg/info dir, then issued the command 'rm cinellera*'.

I then ran 'apt-get dist-upgrade', and now a whole pile of packages  are installing. 
I noticed some initial dignostic messages referring to cinellera, saying something like "list information can't be found. Now assuming that no such package exists". 


YuS!!

Everything has installed.

I just ran 'apt-get update' again for the second time, and there are now no errors.

What were the files that I removed ?

---

### Post by Soul-Sing on 2010-05-21
sorry i messed up the cinerella/cinelerra word....

glad it helped though :)

---

