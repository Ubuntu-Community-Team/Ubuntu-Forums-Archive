---
title: "Ubuntu command to download the .deb file of a package along with its dependencies."
date: 2024-10-03
forum: Installation &amp; Upgrades
---

### Post by prmjh4 on 2024-10-03
I am trying to download the .deb files of a package that is already installed on my Ubuntu Server. 
But I am in need of its .deb files along with all the dependencies packages that are required by that package to get installed with it as well.
For Example: We have the following command in SLES Linux OS to download the packages for lvm2 along with its dependencies packages. 
 "zypper install --download-only lvm2"
The output was the list of packages that was obtained for lvm2 along with the dependencies packages that are required for lvm2 to function without any issues.
So, I  am looking for a similar command in Ubuntu as well to achieve the same task.

---

### Post by TheFu on 2024-10-03
Synaptic will let you create a list of all the dependencies for a package.
*File --> Generate Package Download Script*

---

### Post by ian-weisser on 2024-10-03
Start from a LiveUSB's "Try Ubuntu" environment, available on both Desktop and server.

This prevents haywiring your existing system. You can use the LiveUSB on any other convenient hardware to obtain the answers.
It lets apt start at a commonly-defined point (fresh install), preventing surprises later. "Drat, that wasn't on my list!"


For a mere list of packages
```

sudo apt update
apt install --simulate <package_name>         // sudo is not required for simulate

```


To download the packages into /var/cache/apt/archives
```

sudo apt update
sudo apt install --download-only <package_name>

```


Alternately, you can query the working system, though sometimes the answers may be incomplete or misleading, depending upon what else might be installed.
The list of packages and subsequently orphaned dependencies on your current system:
```

apt --simulate autoremove <package_name>     // sudo is not required for simulate

```


Or you can ask apt for the first level of dependencies, and tediously iterate through each of those for subsequent levels.
```

apt depends <package_name>                // sudo not required for dependency queries

```

---

