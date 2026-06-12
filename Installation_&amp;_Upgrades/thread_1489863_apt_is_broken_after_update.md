---
title: "apt is broken after update"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by larscwallin on 2010-05-21
Hi,
Please help me out with this if you can.

When updating my Ubuntu 10.4 using the update manager the process broke my apt!

During the update process i got the following message (translated using Google unfortunately but i think you get the message):

"Preparing to replace update-manager-core 1:0.134.7 (with .../update-manager-core_1 3a0.134.8_i386.deb%) ...
Unpacking replacement update-manager-core ...
dpkg: .. / .. / src / archives.c: 763: tarobject: Declaration "r == stab.st_size" false.
E: Sub-process / usr / bin / dpkg exited unexpectedly"

Now all apt related stuff fails, including using Synaptics repair of broken packages.

When i run "sudo dpkg --configure -a" i get:

"dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.134.8), but:
  Package update-manager-core is not installed.
dpkg: error processing update-manager (- configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-manager"

How can i fix apt without apt?


Thanks for any tips,
Lars

---

### Post by arrange on 2010-05-21
Is it this bug?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524919](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524919)

---

### Post by larscwallin on 2010-05-22
Thanks :)

I dont think its the same bug. 
According to Synaptic its the update-manager which is broken.

If you look at this:

"dpkg: dependency problems prevent configuration of update-manager:
update-manager depends on update-manager-core (= 1:0.134.8), but:
Package update-manager-core is not installed."

It seems that the component update-manager-core is outdated. Now here comes the ironic part: I cant update update-manager-core  using the update-manger because the new update-manager depends on the new update-manager-core to work! :p

Can i download the update-manager-core component and install it manually?

Thanks again,
Lars

---

### Post by arrange on 2010-05-22
I think it's *dpkg* which is broken here, and that makes it much more difficult to solve.

The question is: do you use encryption for partition data?

---

### Post by larscwallin on 2010-05-22
Nope, no encryption...
Can i use LiveCD for recovery maybe?

---

### Post by arrange on 2010-05-22
Try installing the package manually from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)```

sudo dpkg -D163 -i /var/cache/apt/archives/update-manager-core_1 3a0.134.8_i386.deb > /tmp/dpkg.log

```Post any output here, and also contents of */tmp/dpkg.log* somewhere (f.e. on [Ubuntu pastebin]("http://paste.ubuntu.com/") - it might be very long).

---

### Post by larscwallin on 2010-05-22
Thanks :)

I am not sure what happened but the output in the terminal was this:

[http://paste.ubuntu.com/437910/](http://paste.ubuntu.com/437910/)

This is what ended up in the dpkg.log file (again, translated by google):

"(Reading database ... 237 257 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.134.7 (with .../update-manager-core_1 3a0.134.8_i386.deb%) ...
Unpacking replacement update-manager-core ..."

Any ideas? :)

---

### Post by dino99 on 2010-05-22
first clean the system:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

with such issue, you have to erase the package then update upgrade

---

### Post by arrange on 2010-05-22
?Could you give me the output of```

stat /usr/lib/python2.6/dist-packages/UpdateManager/Core/utils.py /usr/share/pyshared/UpdateManager/Core/utils.py
md5sum stat /usr/lib/python2.6/dist-packages/UpdateManager/Core/utils.py

```(looks like *dpkg* gets stuck on this one)

---

### Post by larscwallin on 2010-05-22
Ok, its fixed!

Turns out that the utils.py file in the UpdateManager folder was named utils.py.dpkg_new

I guess that this file should have been renamed during the upgrade process but failed to do so. Anyway, once i renamed the file to utils.py and ran "upate-manager -c" from the terminal it all worked fine :D 

Thanks a million for all your help!
/Lars

---

