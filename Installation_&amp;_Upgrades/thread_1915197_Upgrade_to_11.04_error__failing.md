---
title: "Upgrade to 11.04 error / failing"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2012-01-25
I'm trying to upgrade my 10.10 to 11.10 (via 11.04)

But after the "setting New Software Channels" I get the following error box when upgrading to 11.04:

```
Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report
```Any suggestions on where to look to fix this?
Or is it just easier to do a clean install?

---

### Post by jerrrys on 2012-01-26
"Unofficial software packages not provided by Ubuntu"

PPA's; third party software sources could be the cause.

---

### Post by solitaire on 2012-01-28
Tried removing all PPA's and running "Computer Janitor" to remove all unofficial packages, 

Still no difference!!

Still getting the same error

Looks like it's a Wipe and reinstall :(

Unless anyone else has any ideas?????

---

### Post by BC59 on 2012-01-28
Did you run sudo dpkg --configure -a and sudo apt-get -f install to ensure all necessary packages are completely installed and configured?

---

### Post by solitaire on 2012-01-28
Ran both commands.
Everything was installed and configured correctly!

---

### Post by BC59 on 2012-01-28
If you run```
sudo apt-get --fix-missing install
sudo apt-get -f upgrade
``` what is the result?:

---

### Post by solitaire on 2012-01-28
> **BC59 said:**
> If you run```
sudo apt-get --fix-missing install
sudo apt-get -f upgrade
``` what is the result?:

Here's what I get:

```

bill@Ion:~$ sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bill@Ion:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bill@Ion:~$ 
```

Everything looks OK!

---

### Post by BC59 on 2012-01-28
Check your graphics driver, if you use proprietary driver, reinstall it.

---

### Post by BC59 on 2012-01-28
In this thread in the final posts they propose some solutions:
[http://ubuntuforums.org/showthread.php?t=1592083](http://ubuntuforums.org/showthread.php?t=1592083)

---

### Post by solitaire on 2012-01-28
no nswrapper (or however you spell it)removed noveau as well


no difference, same error


looking like a wipe and reinstall job!!!!

---

### Post by BC59 on 2012-01-28
Should be a good idea to report the bug as it's stated to the error message
> If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report

---

### Post by solitaire on 2012-01-28
think i'll have to report a bug.
Just need to remember how to use tar using the command line now! lol

---

### Post by solitaire on 2012-01-28
reported bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/923172](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/923172)

Don't know now wither to leave my system in a mess till i get feedback on the bug or just wipe it and start from scratch!!

---

