---
title: "Maverick Meerkat upgrade crashes half way"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by jim.cat on 2010-11-08
Hello,

I was upgrading my system... but it crashed and the updater just disappeared... I have not rebooted because I assume my system is a mess right now and won't load... 

I was updating from 10.04 to 10.10, there is any command to allow me resume the upgrade process?... before I shut down and all becomes very messy? 

Thanks!

SORTED:
> **jim.cat said:**
> right this worked :grin: 

so if anybody reads it run the following comands until they finish clean:

```

$ sudo apt-get install -f  -> Tries to fix the apt-get system
$ sudo dpkg --configure -a   -> Tries to fix the dpkg system

```If you get stuck because some of them hang or says they are lock ==> Delete the lock file
```
$ sudo rm /var/lib/dpkg/lock 
```or
```
$ sudo rm/var/cache/apt/archives/lock
```
Finally finish the update using: 

```
$ sudo apt-get dist-upgrade
```if it stops/crashes at any time (it did to me twice) run the whole process again :smile: on the update you might need to answer diferent dialogs :smile: 

Finally just to double check i would run 

```

$ sudo apt-get install -f  -> Tries to fix the apt-get system
$ sudo dpkg --configure -a   -> Tries to fix the dpkg system
$ sudo apt-get dist-upgrade

```and double check all 3 finish clean (0 updates 0 installs and no errors) :razz: and reboot and u will be done :grin: 

At least that worked for me!

---

### Post by sikander3786 on 2010-11-08
There is actually no way of resuming the upgrade straight away. You need to switch on your PC and see how far can you go, if it was just at the process of downloading updates, it should boot just fine. If it has done some installation, it might/might not boot to the desktop.

Please see what is happening there and report back. We'll like to know any errors you come across during the process.

---

### Post by jim.cat on 2010-11-08
I know for  certain it was installing packages and that it was about 20-30%. It must be some way of doing something other than reboot and have a dead system...

---

### Post by sikander3786 on 2010-11-08
> **jim.cat said:**
> I know for  certain it was installing packages and that it was about 20-30%. It must be some way of doing something other than reboot and have a dead system...
I fear if it doesn't work with a reboot, you might need to backup all your files and reinstall Ubuntu as I have seen that happening quite a few times and most of the time, recovery was unsuccessful.

If you can get into a recovery console, you can try some commands. You need to know what you can do with that system for now.

The only option left if it is unbootable is to boot a Live CD, mount your Ubuntu partition and backup all of your important data before installing a fresh copy.

I don't know anything else that you can do without booting your PC :-) You can wait for some other replies and see if they can help you.

---

### Post by jim.cat on 2010-11-08
> **sikander3786 said:**
> (...)If you can get into a recovery console, you can try some commands. You need to know what you can do with that system for now.(...)

I have been having this system since 6.06 and is doing thousands of things, reinstall is so not a solution... it would be really surprising to me that there is not any way of reinitiate the upgrade to 10.10... I must not be the only one in this situation...

---

### Post by jim.cat on 2010-11-08
I've runned this:

$sudo apt-get -f install

and apparently it installed some upfdates :S I suppose formerly from 10.10 since has redone the kernels and grub. 

After this I have been able to use:

$sudo apt-get dist-upgrade

wich seems that is resuming the upgrade and installing the rest of the packages. Does anybody used this before after a broken upgrade? Is it the right thing to do?

---

### Post by sikander3786 on 2010-11-08
> **jim.cat said:**
> For now I've found this:

sudo apt-get -f install

it seems that is resuming the upgrade. Does anybody used this before after a broken upgrade? Is it the right thing to do?
Sorry, Excuse me. I got it wrong. You mentioned the updater crashed in your 1st post and I thought it was the computer which crashed. Thanks God you didn't reboot following me :-)

```
sudo apt-get install -f
```

That is a command to install missing dependencies. Safe to do.

In addition to that

```
sudo dpkg --configure -a
```

might help. Please post the output.

---

### Post by jim.cat on 2010-11-08
good good 

it seems that 

```
$sudo apt-get dist-upgrade 
```

is properly upgrading it now :) 

shall i run the

```
$ sudo dpkg --configure -a 
```

once it finishes for more safety?

---

### Post by jim.cat on 2010-11-08
right this worked :D 

so if anybody reads it run the following comands until they finish clean:

```

$ sudo apt-get install -f  -> Tries to fix the apt-get system
$ sudo dpkg --configure -a   -> Tries to fix the dpkg system

```

If you get stuck because some of them hang or says they are lock ==> Delete the lock file
```
$ sudo rm /var/lib/dpkg/lock 
```
or
```
$ sudo rm/var/cache/apt/archives/lock
```


Finally finish the update using: 

```
$ sudo apt-get dist-upgrade
```

if it stops/crashes at any time (it did to me twice) run the whole process again :) on the update you might need to answer diferent dialogs :) 

Finally just to double check i would run 

```

$ sudo apt-get install -f  -> Tries to fix the apt-get system
$ sudo dpkg --configure -a   -> Tries to fix the dpkg system
$ sudo apt-get dist-upgrade

```

and double check all 3 finish clean (0 updates 0 installs and no errors) :P and reboot and u will be done :D 

At least that worked for me!

---

