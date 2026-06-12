---
title: "From 14.04 LTS to 16.04 LTS"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by tb75252 on 2016-04-22
I have 14.04 LTS installed on my PC and would like to upgrade to 16.04 LTS.

Am I reading these release notes correctly?
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes?_ga=1.53832616.166235725.1459944910](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes?_ga=1.53832616.166235725.1459944910)

They seem to state that if I want to upgrade to 16.04 LTS using Software Updater I have to wait three months from now...

---

### Post by RobGoss on 2016-04-22
Well in my opinion I think it's best to just do a fresh install of 16.04, save your self time and trouble

Installing from 1404 to 1604, you might run into issues. I went from 14.04 to a fresh install of 16.04 and its all good

---

### Post by oldfred on 2016-04-22
Normally the gui/Software updater does not offer to update LTS versions until first point release. That is since LTS users primarily want stability.

If you want to update you can force it with command line. You do have to make sure proprietary drivers and ppas are turned off. If not available with 16.04 yet they hang install and create many issues. You can just re-add them after upgrade. Sometimes ppa not required with newer install, also.

But I am like RobGoss and add another 25GB / (root) partition on SSD and install to that. I still have my 14.04, but convert to my 16.04 once fully configured. All data is in separate /mnt/data partition on HDD, so I can have smaller / partitions.

---

### Post by RobGoss on 2016-04-22
**Fred** is correct, you can force it to upgrade using the terminal but that did not work out well for me 

I was getting graphic card error when ever I try to boot up my machine and couldn't get past that message, so I did a clean install and never look back

I run all my distributions on 160 GB and some on 500 GB storage because  I'm in process of converting over to Linux full-time

---

### Post by rosswmcgee on 2016-04-22
Does anyone know when the first point release is?

---

### Post by claracc on 2016-04-22
You will have to wait for about three months to obtain the 16.04.01 release.

---

### Post by kc1di on 2016-04-22
About 3 Months is normal. 
I would back up every thing to an external drive, the cloud or DVD /usb stick and do a fresh install.

---

### Post by PaulW2U on 2016-04-22
> **claracc said:**
> You will have to wait for about three months to obtain the 16.04.01 release.
Which I'm led to believe will be the best time to upgrade from Trusty to Xenial.

I know that one flavour has not gone overboard to test upgrades from Trusty to Xenial as there have there been a number of problems in doing so. Such problems should be resolved by the time of the **first** point release which I understand is the earliest time that you should upgrade from one LTS release to the next.

---

### Post by mickee384 on 2016-04-22
can I upgrade to 15.10, then the 16.04 will show in the updater?. I am 14.04. Been so long as I used to do all upgrades... now was just doing LTS...

---

### Post by tb75252 on 2016-04-22
But how will I keep all my customizations if I do a fresh install?

---

### Post by rmisk on 2016-04-22
When upgrading from 14.04 to 16.04 I discovered problems with 4.9 versions of gcc-doc and cpp-doc.  I cannot remove, reinstall, nor upgrade either package.  Whatever I try with apt-get and dpkg (using all of the forced options I can find) I get responses similar to:

sudo dpkg --remove --force-remove-reinstreq cpp-doc
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 747208 files and directories currently installed.)
Removing cpp-doc (4:4.9-1ubuntu7) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing package cpp-doc (--remove):
 subprocess installed pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cpp-doc

Any ideas on how I can remove or upgrade these packages?

---

### Post by rmisk on 2016-04-23
Solved by using:
$ locate cpp-doc
$ sudo rm -rf <all files and folders found by locate>
$ sudo apt install cpp-doc

---

### Post by RobGoss on 2016-04-23
Glad you found a fix for this and thank you for sharing your solution with the forum, Would you mind marking this post as solved, You can do this by using the **Thread Tool tab** at the top of this post. Thanks so much

---

