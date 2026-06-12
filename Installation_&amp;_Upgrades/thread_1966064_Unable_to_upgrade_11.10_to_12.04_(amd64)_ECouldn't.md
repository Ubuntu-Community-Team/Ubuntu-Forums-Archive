---
title: "Unable to upgrade 11.10 to 12.04 (amd64): E:Couldn't configure pre-depend libtinfo5"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Artemis3 on 2012-04-26
I'm getting this error:

> 'E:Couldn't configure pre-depend libtinfo5 for libncurses5, probably a dependency cycle.'

And the upgrade cancels reverting the changes.

---

### Post by jadtech on 2012-04-26
try these  one by one 
```
 sudo apt-get update 
sudo apt-get install apt python-apt
sudo do-release-upgrade
```

thoughI guess it not necessary I do a reboot after the python install
see how that goes

---

### Post by jadtech on 2012-04-26
not sure whatthe reason but there is a issue with depking  the upgrade for some python apt is nessary to install some libaries required  but the python apt unpacks later in the install so everything ends up failing ..


i concider your case fortunate  for most the install continues and then on restart the first time there is a load of varied problems from no graphic or guis video that is agfull mouse and touch pads that dont work no keyboard ..

---

### Post by Artemis3 on 2012-04-26
I have apt and python-apt already installed...

---

### Post by Artemis3 on 2012-04-27
bump

---

### Post by P Panon on 2012-04-28
You might want to try the instructions on entry #23 at bug report 924079 [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079)

---

### Post by jadtech on 2012-04-28
if python-apt has installed then continue the upgrade  to finish and the packages that had dependancy issues can install .

try this
```
 sudo apt-get dist-upgrade -f 
```

hopefully this help this is a known upgrade bug for some  packages unpack in a wrong order or server drops sa package or 2 because it is over loaded  what ever the cause ..

---

### Post by Artemis3 on 2012-04-28
It appears to be related to bug [#924079](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079) and will proceed with this workaround: [http://aaron-kelley.net/blog/2012/04/upgrade-from-ubuntu-11-10-oneiric-to-ubuntu-12-04-lts-precise-fails-with-error-couldnt-configure-pre-depend-libtinfo5-for-libncurses5-probably-a-dependency-cycle/](http://aaron-kelley.net/blog/2012/04/upgrade-from-ubuntu-11-10-oneiric-to-ubuntu-12-04-lts-precise-fails-with-error-couldnt-configure-pre-depend-libtinfo5-for-libncurses5-probably-a-dependency-cycle/)

**Success!** The workaround allowed me to upgrade.

The workaround is simply to install [libtinfo5](http://packages.ubuntu.com/precise/libtinfo5), [libncurses5](http://packages.ubuntu.com/precise/libncurses5), and [libncursesw5](http://packages.ubuntu.com/precise/libncursesw5) from precise in oneiric before the upgrade.

---

