---
title: "Upgrade ubuntu 16.04 LTS to 18.04 LTS on dual boot system"
date: 2018-10-15
forum: Installation &amp; Upgrades
---

### Post by saimonas54 on 2018-10-15
Hello. 

I am totally new in ubuntu systems, so I have some basic questions. 

I have my work computer with two drives. 1. SSD drive with windows7. 2. HDD drive with ubuntu 16.04 LTS.

I just need to upgrade ubuntu 16.04 LTS to 18.04 LTS, but without any files losing.

Can I just write these 3 commands to the terminal and upgrade my system without files losing?

Thank you for help!

$ sudo apt update 
$ sudo apt upgrade
$ sudo apt dist-upgrade

---

### Post by Autodave on 2018-10-15
Yes, you can do that. However, upgrading is NEVER a 100% sure thing.  You need to back up EVERYTHING before you start!!  Get the files you need to keep to an external source. (You should have them backed up anyway.)

---

### Post by ajgreeny on 2018-10-15
You can certainly run command ```
sudo apt dist-upgrade
``` but it will not move you from 16.04 to 18.04.
I think it will just update the kernel version to the highest version available.

I have never upgraded from one distro version to the next and can not remember the command that is now used (**do-release-upgrade** I think but don't take my word for it)   Like Autodave I have always thought it too risky so do a clean install.

---

### Post by oldfred on 2018-10-15
And whether you do an upgrade or clean install, you must have a good backup (or two).
Make sure backup includes all of /home, list of installed apps and perhaps some configuration files in /etc if you manually edited anything. I only edit a couple like grub, 40_custom & /etc/exports. But I just  copy those into /home so my backup of it includes those and I can then compare new defaults with my settings. And if server or server apps, you may have those in / folders and need separate backups.

Those that upgrade find it works if they have a fully updated system before upgrade, including housecleaning old kernels & log files.
And have removed any proprietary drivers like nVidia or WiFi and all ppas.
If ppa not found in new version install stops at that point and then you have a broken system.

I used to do upgrades but found clean install does a more thorough housecleaning and defaults normally work. Some old settings may or may not be correct  when system updated.  But I cheat & install to another 25GB / (root) partition as my data is in other partitions. Then I have way to confirm my backups are good, but have old install to go back to if needed.

---

