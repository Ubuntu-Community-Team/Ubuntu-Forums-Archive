---
title: "Preseeding: Can't access cdrom?"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by Beacon11 on 2012-09-18
Hey all. At work we often need to install Ubuntu Server and several extra packages while offline. To make this faster, I'm creating a custom Ubuntu Server install via preseeding (following this documentation: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)). Installing extra packages was easy and works well.

In addition to adding a few packages, I would like to add another repository to the default set. This is where it seems to get tricky. Remember that, at install time, these computers are offline. However, I need to add an online repository to the list along with adding its key. Adding the repo to the list is easy with

```
d-i   apt-setup/local0/repository string <repo url>
```

But the key NEEDS TO BE ADDED OFFLINE. I downloaded the key and added it to the ISO (I made a new "keys" directory), but I can't seem to be able to access /cdrom from the preseed file. The simplest test is a late_command:

```
d-i   preseed/late_command string df > /target/home/df.txt; ls -Rl /cdrom > /target/home/cdrom.txt; ls -Rl /target/media/cdrom > /target/home/target_cdrom.txt
```

The server install tells me the above command exits with error code -1, and the only file out of those three that contains anything is the df, which looks like this:

```

Filesystem             1K-blocks     Used   Available   Use%   Mounted on
none                      205182      180      204992     0%   /run
devtmpfs                 1020212        8     1020204     0%   /dev
/dev/sr0                 1408470  1408470           0   100%   /cdrom
/dev/mapper/ubuntu-root 18540428  3541660    14068568    20%   /target
/dev/sda1                 233191    24991      195759    11%   /target/boot
/dev/mapper/ubuntu-root 18540428  3541660    14068568    20%   /dev/.static/dev
devtmpfs                 1020212        8     1020204     0%   /target/dev
/dev/sr0                 1408470  1408470           0   100%   /target/media/cdrom

```

So obviously both /cdrom and /target/media/cdrom exist. Why can't I read them from the preseed file? Is there any other way to add this key without needing to download it like the following?

```
d-i   apt-setup/local0/key string <repo key url>
```

Thank you for your help.

---

### Post by dino99 on 2012-09-18
you might ask devs directly on askubuntu

---

### Post by Beacon11 on 2012-09-18
Devs are more likely to look on AskUbuntu than these forums? I guess I'm not really familiar with which I should be using nowadays.

Thanks for the heads up! The post is here: [http://askubuntu.com/questions/190200/preseeding-cant-access-cdrom](http://askubuntu.com/questions/190200/preseeding-cant-access-cdrom)

---

