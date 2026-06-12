---
title: "Does Not Upgrade"
date: 2022-11-11
forum: Installation &amp; Upgrades
---

### Post by lawrence-joy on 2022-11-11
I have version 22.04 with the message that 22.04.1 is available. When I click on "Upgrade" the system goes to the puma? face (head) and does nothing. What do I do to get the upgrade to implement 22.04.1?

---

### Post by Bashing-om on 2022-11-11
lawrence-joy; Hey -

How about trying the upgrade from terminal:
```

sudo apt update
sudo apt upgrade

```

This way in the event of errors - the kernel will tell.

[INDENT]there is a process
[/INDENT]

---

### Post by Impavidus on 2022-11-12
22.04.1 is just 22.04 with all the updates until the end of July 2022 applied. Its not a new release (although a new live disk image was released), so there's no upgrade from 22.04 to 22.04.1. The same goes for the other point releases (where only the third number changes). So I don't know what this is about. Anyway, Bashing-om's commands above should tell if there's any problem and what relaese you're actually running. Please show us the whole output.

---

### Post by lawrence-joy on 2022-11-12
I did those two lines of commands in the terminal and that looks like the problem is solved. Here is the output:
larry@larry-MS-7693:~$ sudo apt update
[sudo] password for larry: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Hit:4 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) focal InRelease           
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
larry@larry-MS-7693:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libclang-common-10-dev libclang-common-12-dev libclang-cpp11 libfwupdplugin1
  libllvm10 libxmlb1 shim
Use 'sudo apt autoremove' to remove them.
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages have been kept back:
  mesa-opencl-icd
The following packages will be upgraded:
  bolt gnome-software gnome-software-common gnome-software-plugin-snap
  ubuntu-software
5 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 6,678 kB of archives.
After this operation, 37.9 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 bolt amd64 0.9.1-2~ubuntu20.04.1 [143 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software-plugin-snap amd64 3.36.1-0ubuntu0.20.04.1 [73.0 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software amd64 3.36.1-0ubuntu0.20.04.1 [893 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software-common all 3.36.1-0ubuntu0.20.04.1 [5,559 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 ubuntu-software all 3.36.1-0ubuntu0.20.04.1 [10.7 kB]                                                                              
Fetched 6,678 kB in 15s (444 kB/s)                                                                                                                                                                        
(Reading database ... 609935 files and directories currently installed.)
Preparing to unpack .../bolt_0.9.1-2~ubuntu20.04.1_amd64.deb ...
Unpacking bolt (0.9.1-2~ubuntu20.04.1) over (0.8-4ubuntu1) ...
Preparing to unpack .../gnome-software-plugin-snap_3.36.1-0ubuntu0.20.04.1_amd64.deb ...
Unpacking gnome-software-plugin-snap (3.36.1-0ubuntu0.20.04.1) over (3.36.1-0ubuntu0.20.04.0) ...
Preparing to unpack .../gnome-software_3.36.1-0ubuntu0.20.04.1_amd64.deb ...
Unpacking gnome-software (3.36.1-0ubuntu0.20.04.1) over (3.36.1-0ubuntu0.20.04.0) ...
Preparing to unpack .../gnome-software-common_3.36.1-0ubuntu0.20.04.1_all.deb ...
Unpacking gnome-software-common (3.36.1-0ubuntu0.20.04.1) over (3.36.1-0ubuntu0.20.04.0) ...
Preparing to unpack .../ubuntu-software_3.36.1-0ubuntu0.20.04.1_all.deb ...
Unpacking ubuntu-software (3.36.1-0ubuntu0.20.04.1) over (3.36.1-0ubuntu0.20.04.0) ...
Setting up gnome-software-common (3.36.1-0ubuntu0.20.04.1) ...
Setting up gnome-software (3.36.1-0ubuntu0.20.04.1) ...
Setting up bolt (0.9.1-2~ubuntu20.04.1) ...
bolt.service is a disabled or a static unit not running, not starting it.
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.6-1~ubuntu20.04.4) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for dbus (1.12.16-2ubuntu2.3) ...
Setting up ubuntu-software (3.36.1-0ubuntu0.20.04.1) ...
Setting up gnome-software-plugin-snap (3.36.1-0ubuntu0.20.04.1) ...
larry@larry-MS-7693:~$ 

Thanks again for the help.:KS If there is something I should be aware of in the output please let me know, otherwise, as far as I can tell, it's fixed.

---

### Post by Impavidus on 2022-11-12
So you're on 20.04. This can be upgraded to 22.04. 20.04 still has a long time of support left, but you may prefer the more recent software on 22.04.

You can only upgrade to another release of Ubuntu when all packages are fully upgraded. In your case, an upgrade to mesa-opencl-icd is available and not installed. Upgrade that first:```
sudo apt upgrade mesa-opencl-icd
```If that appears to do something alarming, cancel it. If you get some error, report it.

Third-party repositories will be disabled during a release upgrade. To be sure it all works, you can disable your deadsnakes repository before attempting the upgrade. It can be re-enabled later, provided that repository is available for 22.04. You can also clean up by removing those autoremovable packages. Unless you actually need them; then mark them as manually installed.

Sometimes something goes wrong during a release upgrade. Some people have more success than others. Fixing a release upgrade gone wrong can be very hard, too hard to even attempt, so it's best to be prepared for a fresh install anyway. And make sure you've got backups of all important files, as always.

---

### Post by mIk3_08 on 2022-11-12
[QUOTE=lawrence-joy]Thanks again for the help.:KS If there is something I should be aware of in the output please let me know, otherwise, as far as I can tell, it's fixed.                 [/QUOTE]
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

