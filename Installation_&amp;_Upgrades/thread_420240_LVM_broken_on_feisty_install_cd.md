---
title: "LVM broken on feisty install cd ?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by chris_s on 2007-04-23
Hi,
did any one tried an installation, using LVM (and the alternate install-cd)?
It seems that the installer-cd can not activate existing volume-groups. I tried an additional installation on my laptop and there is already a LVM-group. When the partitioner tries to activate this group, it stalls there and does not go any further. I tried to activate the group manually (modprobe dm-mod && vgchange -a y), but the vgchange-process stalls and it is not possible to interrupt it.
I did not try to create a new volume-group that far, as I have no additional hdd that fits for my thinkpad.

greetings, Chris

---

### Post by raidensix on 2007-04-23
It's just painfully very slow in activating an existing volume set. I left mine alone for about 30mins and it eventually activated.

---

### Post by pmocek on 2007-05-08
see also: [Ubuntu 7.04 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/704")
> 
On the alternate or server CDs, creating LVM logical volumes will take some time to complete and may appear to have stopped completely. There is no need to take any action, the installation will continue after approximately three minutes for each volume configured. [Bug #105623]("https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623").

---

### Post by pmocek on 2007-05-08
see also: [Bug #105623: "udev rules missing from udeb"]("https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623")

---

