---
title: "HOWTO: Rescue broken Dapper -&gt; Edgy upgrade"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by vyruss on 2006-11-02
I posted this to help somebody who had trouble with his upgrade, but I thought it may come in handy for more people, so I'm posting it here too. My apologies if it doesn't belong here.

---

First of all **don't panic**, nothing is wrong with your ***partitions***. It's probably just that you didn't use the ***recommended*** upgrade method!

(see **[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)** and **[http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html)**)

**Find an Ubuntu Desktop (live) CD and boot your PC with it.**

Then **open a console window and do** this: ```
sudo su
```. Then make a **mountpoint** for your ubuntu partition e.g. if your ubuntu installation is on /dev/hda2 then: ```
mkdir /mnt/a
mount /dev/hda2 /mnt/a
```

Now you have to sort-of "login" to your installation to complete your upgrade by doing this:```
**chroot** /mnt/a
```

You are now at the root directory of your almost-upgraded ubuntu installation. **You can now start doing things to complete the upgrade & rescue your system**.

Try running these now:```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

If things go wrong, apt-get will tell you more or less what the problem is.

Usually **you will have to run these** commands a few times:```

apt-get -f install
dpkg --configure -a
```

And **these may also come in handy** for problems:```

apt-get -f remove
apt-get autoremove
```

**Remember**, you may have to run these commands **many times each**, and not always in the above order, depending on what is needed. Generally the basic rule is that a few packages have upgraded properly, so it's best to remove them and reinstall them. The most basic packages you need installed are: **ubuntu-minimal, ubuntu-standard, ubuntu-desktop and xserver-xorg**.
Good luck and get to work! :)


**P.S.:** You will also find **these links** helpful:
**[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)** (**very** helpful)
**[http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-apt-get/](http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-apt-get/)**
**[https://launchpad.net/distros/ubuntu/+bug/57121](https://launchpad.net/distros/ubuntu/+bug/57121)**

---

