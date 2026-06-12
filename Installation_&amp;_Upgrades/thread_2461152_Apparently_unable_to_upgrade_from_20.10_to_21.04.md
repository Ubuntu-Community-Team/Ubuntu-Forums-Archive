---
title: "Apparently unable to upgrade from 20.10 to 21.04"
date: 2021-04-25
forum: Installation &amp; Upgrades
---

### Post by josefranw on 2021-04-25
I have used the Software and Updates program as well as tried the command line to upgrade my Ubuntu version (20.10) to the new available one (21.04) and there is nothing to update/upgrade. I am wondering why. Am I doing something wrong?

This is what I get in the command line:

pachico@pachico-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I do have it configured to notify on any new version available (as opposed to only LTS versions)

I am no new to Ubuntu though, it's been a while since I last used it. (I didn't have a laptop for a long time...)

---

### Post by deadflowr on 2021-04-25
You're doing nothing wrong, other than the command is wrong for release upgrades.
Proper command is do-release-upgrade.

But that said, the upgrade channel has not been enabled yet, as per the release notes:
[https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221]("https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221")
> Release Upgrades
Upgrades from Ubuntu 20.10 to Ubuntu 21.04 are not enabled as it is possible for some systems to end up in an unbootable state if they use EFI version 1.10 - bug 1925010. 283 Release upgrades will be enabled once an updated version of shim is available which is compatible with EFI version 1.10.

---

### Post by coffeecat on 2021-04-25
You're not alone. I'm seeing the same. Have a look at this post from guiverc in another thread which explains:

[https://ubuntuforums.org/showthread.php?t=2461018&p=14033588&viewfull=1#post14033588](https://ubuntuforums.org/showthread.php?t=2461018&p=14033588&viewfull=1#post14033588)

**Edit**: ninja'd by deadflowr.

---

### Post by Impavidus on 2021-04-26
It's normal (and has been for years) that the upgrade path from one Ubuntu version to the next gets opened between 3 and 15 days after release of that next version. Except for LTS to LTS upgrades, which are only enabled about 3 months after release.

Sometimes it takes longer. Don't be hasty.

---

### Post by grahammechanical on 2021-04-26
Please run this command

```
man apt-get
```

and read what the manual says about the dist-upgrade command.

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and **it will attempt to upgrade the most important packages at the expense of less important ones if necessary**. The dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

The dist-upgrade command can break things as well as fix things.

Regards

---

### Post by josefranw on 2021-04-26
Thanks for the answers. I understand, now.

---

