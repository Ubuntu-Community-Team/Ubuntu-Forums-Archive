---
title: "Ubuntu clean upgrade instructions"
date: 2019-06-30
forum: Installation &amp; Upgrades
---

### Post by Edward_Diener on 2019-06-30
In trying to upgrade from Ubuntu 18.04 to 19.04 I am trying to follow the instructions about doing a Clean Upgrade at [https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade). In the instructions it is telling me to remove the packages in the "Installed ( local or obsolete ) " status section in Synaptic. However one of the package listed in this section is 'network-manager' and its supporting files. If I try to remove this package I am told that 'gnome-control-center' and 'ubuntu-desktop' packages must also be removed among others. Can this be right to remove this package in preparation for an upgrade ? Furthermore "libnm*' packages are also listed in this section and removing them also removes 'gnome-shell' among other gnome packages. Can it really be right to remove all these packages in this Synaptic status section prior to attempting an upgrade ?

---

### Post by Xian on 2019-06-30
The program network-manager is a supported application in 19.04.

[https://packages.ubuntu.com/disco/network-manager](https://packages.ubuntu.com/disco/network-manager)

If it shows among your local/obsolete list it may be an unknown version or a repo issue. 

What is the output of this command?:

```
sudo apt-get install --reinstall network-manager
```

---

### Post by Edward_Diener on 2019-07-02
> **Xian said:**
> The program network-manager is a supported application in 19.04.

[https://packages.ubuntu.com/disco/network-manager](https://packages.ubuntu.com/disco/network-manager)

If it shows among your local/obsolete list it may be an unknown version or a repo issue. 

What is the output of this command?:

```
sudo apt-get install --reinstall network-manager
```

The output of 

```
sudo apt-get install --reinstall network-manager
```

is

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of network-manager is not possible, it cannot be downloaded
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I am on 18.04, not 19.04. The package is network-manager 1.10.14-0ubuntu2.

---

### Post by Frogs Hair on 2019-07-03
In order to upgrade as stated you would have upgrade to 18.10 first. 19.04 is not an LTS release so there is no direct upgrade path.

---

### Post by Impavidus on 2019-07-04
> **Frogs Hair said:**
> In order to upgrade as stated you would have upgrade to 18.10 first. 19.04 is not an LTS release so there is no direct upgrade path.

True, but it should be noted that in a few weeks, when 18.10 has reached end-of-life, there will be a direct upgrade from 18.04 to 19.04. I don't know how reliable those release upgrades are.

OP, could you show the output of```
apt policy network-manager
cat /etc/apt/sources.list
```That will show where the package manager thinks it can find the network-manager package and what your software sources are.

Also note that the guide you linked too in your first post is quite old. Most of it was written in 2009.

---

### Post by houstonbofh on 2019-07-04
May I suggest something different?  Hard drives are cheap, and my time has value.  Just install to a new (and faster) hard drive and then copy the old apps.  As for what was installed, this is a handy command.
```
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)
```

Details here.
[https://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages](https://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages)

---

