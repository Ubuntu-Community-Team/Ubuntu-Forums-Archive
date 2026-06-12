---
title: "Ubuntu 13.04 doesn't offer upgrade to 13.10"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by csaba-toth on 2013-11-10
I upgraded one of my machines from 12.10 to 13.04. Now I want to upgrade it to 13.10, but when I run the Software Updater, it simply doesn't display the option to upgrade to 13.10.
In the Software Updater Settings I have the "Notify me of a new Ubuntu version:" set to "For any new version".
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

```
So this is not the case when someone starts the upgrade and then it's interrupted.

I haven't seen any repository related or other error messages.
I thought I ask the community before I start to fiddle manually.
On my tablet everything went fine and now it has 13.10.

---

### Post by fantab on 2013-11-10
Keep your 13.10 updated and you will get the 'upgrade to 13.10' option soon. If not then [https://help.ubuntu.com/10.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/10.04/serverguide/installing-upgrading.html)... 13.04 needs to be uptodate.

---

### Post by craig10x on 2013-11-10
Or, you can burn an iso disc of 13.10 and when you run the live session, the installer should offer you (as one of the automatic options) to UPGRADE rather then just do a clean install where everything gets wiped out...this would only be offered if you run only one ubuntu on your computer...so if you do, try it, and do the upgrade from there...

It's the method i always use to upgrade and it works very well... and it is VERY FAST also...installs in about the same amount of time that a clean install would normally...don't forget to turn off any ppas in your software sources before you do it...you can read about my experience with it here:
[http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade](http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade)

---

### Post by csaba-toth on 2013-11-11
Thanks for all the tips. I found this shell command in a guide, and it gonna work. If I invoke the update manager with this -d options, it offers me the 13.10:
```
sudo update-manager -d
```
The guide: [http://www.unixmen.com/upgrade-ubuntu-13-04-raring-ubuntu-13-10-saucy-salamander/](http://www.unixmen.com/upgrade-ubuntu-13-04-raring-ubuntu-13-10-saucy-salamander/)
I haven't tried the ```
do-release-upgrade
``` and other spells, because hopefully I won't need them.

---

