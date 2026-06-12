---
title: "problem with installing firefox updates"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-03-04
Is there some problem with the Canonical/Ubuntu servers ?

There are 4 updates showing as being available for the Firefox program on several of my machines but when the diagonal for software updates is opened I **EVENTUALLY** (the mouse cursor shows the spinning wheel for an inordanent amount of time but does eventually come back to the regular mouse cursor) I get a message in the **CHANGES** tab saying "**Failed to** **download the list of changes**, **Please check your internet connection**".  

However, as far as I can tell my internet connection is working perfectly (demonstrated by my ability to make this post).

If I click on the install updates button the updates appear to download and install perfectly

What is the problem here ?

Thanks.

---

### Post by bapoumba on 2007-03-04
Hello,
what is the error running **sudo update-manager** from a terminal ?

---

### Post by wpshooter on 2007-03-04
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

What does this mean ?

Thanks.

---

### Post by bapoumba on 2007-03-04
Would you happen to be running feisty ?
If so, please check these bug reports:
[https://launchpad.net/ubuntu/+source/software-properties/+bug/71983]("https://launchpad.net/ubuntu/+source/software-properties/+bug/71983")
[https://launchpad.net/ubuntu/+source/software-properties/+bug/84290]("https://launchpad.net/ubuntu/+source/software-properties/+bug/84290")

If edgy, do you have python-vte installed ?
```
~ $ aptitude show python-vte
Package: python-vte
State: installed
Automatically installed: no
Version: 1:0.14.1-0ubuntu1
Priority: optional
Section: python

```

---

### Post by wpshooter on 2007-03-05
I have Feisty install BUT not on one of the machines I am having this problem on.  This problem is occuring on my Dapper machines.

That Feisty machine is connected into the same hub that my other 3 Dapper machines are connected to BUT I have NOT installed SAMBA sharing on the Feisty machine.  The other 3 Dapper machines do have SAMBA installed.

Is it possible for the Feisty machine to be the cause of this problem when it does not have SAMBA installed ?

Thanks.

---

### Post by bapoumba on 2007-03-05
[https://launchpad.net/ubuntu/+source/update-manager/+bug/67999]("https://launchpad.net/ubuntu/+source/update-manager/+bug/67999")
This bug on dapper is also related to missing python-vte (even if the bug description is for problems upgrading to edgy, the error is the same). Could you please check if this package is installed on your dapper machines ?

---

### Post by wpshooter on 2007-03-05
Thanks, I will check tonight when I get home.

Does this mean that if this package is installed, that it needs to be uninstalled ??

And if that is the case, would/will Ubuntu send out an update to fix this or to uninstall the effects of this ?

Thanks.

---

### Post by bapoumba on 2007-03-05
> **wpshooter said:**
> Thanks, I will check tonight when I get home.

Does this mean that if this package is installed, that it needs to be uninstalled ??

And if that is the case, would/will Ubuntu send out an update to fix this or to uninstall the effects of this ?

Thanks.
From the dapper bug report, the package does not come as a dependency, and thus is missing so you should install it.

---

### Post by wpshooter on 2007-03-05
I just checked the machines and the latest version (according to Synaptic) is already installed.

Is it possible that this is a **VERY** recent update and it got installed along with the updates on which I initially had/saw this problem ?

Thanks.

---

### Post by bapoumba on 2007-03-06
If python-vte is installed, then we should look for another explanation. I'll check.

eit: could you provide your source.list file ?

---

### Post by wpshooter on 2007-03-09
I just got back to this.

I will send when I get home tonight.

Thanks.

---

