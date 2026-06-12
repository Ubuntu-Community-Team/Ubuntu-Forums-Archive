---
title: "Error- Encountered a section with no Package"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by rj7 on 2012-11-05
Hi,
I get this error when i try to update my Ubuntu. I have searched the forum and tried the solution give but its of no use..

This is the error i am getting.

```

E: Encountered a section with no Package: header
E: Problem with  MergeList  /var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report. 

```Also i have tried this solution

```

sudo rm /var/lib/apt/lists* -vf  sudo apt-get update  sudo apt-get dist-upgrade
```But still i get the same issue. Thanks for the help in advance.

---

### Post by drpjkurian on 2012-11-05
Please try by unchecking the ppa of Daniel richer 200 in software sources.

---

### Post by rj7 on 2012-11-05
I couldnt open the update manager, synaptic package manager or the software center. When i try to open them i get the error message.
```

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

```

---

### Post by varunendra on 2012-11-06
Please post outputs of :
```
cat /etc/apt/sources.list
ls -1 /etc/apt/sources.list.d
```

---

