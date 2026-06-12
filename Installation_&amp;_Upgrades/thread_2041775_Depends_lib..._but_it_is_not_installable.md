---
title: "Depends: lib... but it is not installable"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by yygyt on 2012-08-13
Hello everyone,

I am using ubuntu 12.04 on my laptop.

Last night I needed to install a package ([octovis]("http://www.ros.org/wiki/octovis")). When I entered the command 

sudo apt-get install ros-fuerte-octovis

I get the following error

```

The following packages have unmet dependencies:
 ros-fuerte-octovis : Depends: libqt4 but it is not installable
                      Depends: libqglviewer-qt4 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

There are some [*suggestions*]("http://ubuntuforums.org/archive/index.php/t-1615221.html") for synaptic package manager, but in 12.04 synaptic package manager does not exist, as far as I know.

[*Here*]("http://ubuntuforums.org/archive/index.php/t-939605.html") one suggests to use apt-get with -f argument to fix broken packages. It didn't solve my problem either.

Can someone guide me to solve this problem?

Thanks in advance.

---

### Post by ajgreeny on 2012-08-13
You can install synaptic without a problem.  Just make sure the universe & multiverse repos are enabled in software-sources, then run ```
sudo apt-get install synaptic
```It's the first addition I make these days as I simply can not function without it.  The USC is a poor, and useless substitute for synaptic when attempting to sort out problems of this sort.

---

