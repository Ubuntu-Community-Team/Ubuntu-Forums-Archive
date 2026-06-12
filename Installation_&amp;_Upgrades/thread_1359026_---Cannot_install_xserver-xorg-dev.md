---
title: "---Cannot install xserver-xorg-dev"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by bzhao on 2009-12-19
I had installed kubuntu 8.04. In adpt, I pressed button(upgrade to new version), the i found that it was upgrading to Ubuntu 9.10, then I close adpt, because I don't want to do that(orignally I think it will do "apt-get disk-upgrade"). Later I did the below command to install new software packages, resutl is a failure.

#apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-dev: Depends: libpixman-1-dev but it is not going to be installed
E: Broken packages


I think that the failure is caused by the previous bad action.
Now I hope to fix the bad case, without reinstall kubuntu.

Thanks!

Bill Z

---

### Post by lemming465 on 2009-12-20
Two of the possible problems are that you may have karmic repositories enabled from the aborted upgrade, and that you may have karmic dependencies downloaded.

Check /etc/apt/sources.list for stray references to "karmic"; for 8.04 all of the enabled repositories (no prefix '#' comment character) should say "hardy".  If it looks messed up, there should be a copy of your previous sources.list kept as /etc/apt/sources.list.save which you could copy back.```
sudo -i
cd /etc/apt
cp sources.list sources.list.oops
cp sources.list.save sources.list
```Once the repositories are known to be OK (you can also look at them graphically in System -> Administration -> Software Sources), try reseting the dependencies by *sudo aptitude clean; sudo aptitude update*

---

