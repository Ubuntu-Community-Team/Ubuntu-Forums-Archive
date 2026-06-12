---
title: "Reinstall Grub2"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by FLCL on 2011-05-17
Hey everyone, was dual booting Ubuntu an Windows, had to reinstall Windows,it wiped out grub, need to reinstall it now. 

Was following this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Trying to reinstall grub with:
```
sudo grub-install --root-directory=/media/d566e91e-941f-4433-8dea-05d3bffb5669 /dev/sda6

```

Gives me the following error:
```
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

*edit more info* Ubuntu is installed on /dev/sda6 on a 50GB partition.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              26       56830   456280064    7  HPFS/NTFS
/dev/sda2   *       56830       56843      102400    7  HPFS/NTFS
/dev/sda3           56843       70981   113561600    7  HPFS/NTFS
/dev/sda4           70981       77826    54979585    5  Extended
/dev/sda5           77096       77826     5859328   82  Linux swap / Solaris
/dev/sda6           70981       77096    49120256   83  Linux

Partition table entries are not in disk order
```

So, I didn't want to do anything and screw things up. I want to boot with grub and not MBR. What should I do? :(

---

### Post by Plueonic on 2011-05-17
> **FLCL said:**
> sudo grub-install --root-directory=/media/d566e91e-941f-4433-8dea-05d3bffb5669[COLOR=Red] /dev/sda6[/COLOR]

Use the Disk device instead of a specific partition to install it to the MBR
```

sudo grub-install --root-directory=/media/d566e91e-941f-4433-8dea-05d3bffb5669[COLOR=Red] /dev/sda[/COLOR]
```

---

### Post by FLCL on 2011-05-17
I'm not certain I follow, it isn't named. Just "50 GB File System". 

So I just install grub to /dev/sda instead of the specific ubuntu partition?

---

### Post by Plueonic on 2011-05-17
> **FLCL said:**
> 
 Ubuntu is installed on /dev/sda6 on a 50GB partition.

> **FLCL said:**
> I'm not certain I follow, it isn't named. Just "50 GB File System". 

So I just install grub to /dev/sda instead of the specific ubuntu partition?
Yes. The ubuntu partition is set as te root directory and the configuration files would be stored there, but the boot loader itself needs to be installed  to the MBR of the device to be picked up during boot. (see the examples in the wiki article you linked above)

---

### Post by Quackers on 2011-05-17
A more normal way to do it is to boot from the live cd and select "try ubuntu" then when the desktop loads open up a terminal and run 
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
which should report no errors.
Then reboot, when Ubuntu should boot directly.
Then open a terminal and run ```
sudo update-grub
``` when you should see the Windows Loader picked up as grub.cfg is run. This will put Windows in the grub menu.

---

### Post by FLCL on 2011-05-17
I'm actually on the live cd now :)

I will go ahead and give it a try

*Edit* Woot! Worked fine, rebooting now :) thank you both very much for the excellent help!

---

### Post by Quackers on 2011-05-17
That's good :-)
Just make sure the Windows Loader is picked up when running sudo update-grub and then you should be good.

---

