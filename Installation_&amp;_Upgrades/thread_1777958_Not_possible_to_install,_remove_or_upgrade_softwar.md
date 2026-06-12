---
title: "Not possible to install, remove or upgrade software"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2011-06-08
I'm helping my mother-in-law with her computer (Ubuntu Lucid) via Remote Desktop. Something has completely borked it. It starts fine but as soon as I try to upgrade, install or remove any software I get the same error that the package depends on linux-headers-2.6.32-31-generic and that linux-headers-2.6.32-31-generic hasn't been installed properly. It says that there's no space left on the drive but *df -h* revealed that there's plenty of room on all partitions. 

I've tried *sudo apt-get update* to update which worked fine but all other commands such as: *sudo apt-get upgrade*, *sudo apt-get -f install*, *sudo apt-get dist-upgrade*, *sudo dpkg --configure -a*, *sudo apt-get purge any packet*, *sudo apt-get remove any packet* and *sudo apt-get install any packet* all results in the same thing. Broken pipe and so on. 

So not a full drive but apt-get complains about no space left, yet it's not possible to uninstall software due to linux-headers-2.6.32-31-generic.

I really would appreciate help with this, because I'm out of ideas now. (Sorry for not having the logs, as the computer is off right now plus it's in Swedish.)

---

### Post by oldos2er on 2011-06-08
Have you tried **sudo apt-get clean** ? It seems odd that there would be a 'no space left on device' error when there actually is enough space. Have you or has she run fsck on all partitions?

---

### Post by 1/0 on 2011-06-08
> **oldos2er said:**
> Have you tried **sudo apt-get clean** ? It seems odd that there would be a 'no space left on device' error when there actually is enough space. Have you or has she run fsck on all partitions?

Yeah, I tried *sudo apt-get clean* and just got a new line. So I figured it was nothing to clean. I haven't tried fsck, since there was nothing alerting in the logs (dmesg) about the drives. I'll try that as soon as she's by the computer again.

---

### Post by 1/0 on 2011-06-08
The drive passed without errors so nope, no problems with the drive...

---

### Post by linuxinstalledfromhdd on 2011-06-08
remotely run

sudo apt-get install bleachbit
sudo bleachbit

Careful not to remove any bookmarks or passwords.

Also you can install Ubuntu-Tweak to clean out any old configuration settings.

---

### Post by 1/0 on 2011-06-08
> **linuxinstalledfromhdd said:**
> remotely run

sudo apt-get install bleachbit
sudo bleachbit

Careful not to remove any bookmarks or passwords.

Also you can install Ubuntu-Tweak to clean out any old configuration settings.

Sorry, no go. Can't install. It only complains on depending on linux-headers-2.6.32-31-generic...

---

### Post by 1/0 on 2011-06-09
Bump

---

### Post by Andrew.Z on 2011-06-09
> **1/0 said:**
> Sorry, no go. Can't install. It only complains on depending on linux-headers-2.6.32-31-generic...

BleachBit or Ubuntu Tweak?  BleachBit upstream package only requires 'menu' and not the Linux kernel headers.  If you think it is BleachBit, please post the terminal output.

By the way, there is a new [BleachBit 0.8.8 beta 2](http://bleachbit.sourceforge.net/news/bleachbit-088beta2)---the first release for Ubuntu 11.04.

---

### Post by avtolle on 2011-06-09
Is there a separate /boot partition? If so, this may be where the "no room" problem is. I'm guessing that your mother-in-law's computer has many kernels installed. If this is so, you should remove old kernels, using Synaptic. Before doing this, though, do ```
uname -r
```from the terminal to establish which kernel is in use (so it isn't removed). Then, try running ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```again.

---

### Post by 1/0 on 2011-06-09
> **Andrew.Z said:**
> BleachBit or Ubuntu Tweak?  BleachBit upstream package only requires 'menu' and not the Linux kernel headers.  If you think it is BleachBit, please post the terminal output.

By the way, there is a new [BleachBit 0.8.8 beta 2](http://bleachbit.sourceforge.net/news/bleachbit-088beta2)---the first release for Ubuntu 11.04.

I can't install any of them. I've tried various packages but none of them will install and none of the installed packages will purge or be removed. Apt-get just complains on dependencies, which is weird. 

> **avtolle said:**
> Is there a separate /boot partition? If so, this may be where the "no room" problem is. I'm guessing that your mother-in-law's computer has many kernels installed. If this is so, you should remove old kernels, using Synaptic. Before doing this, though, do ```
uname -r
```from the terminal to establish which kernel is in use (so it isn't removed). Then, try running ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```again.

No, I created a separate home partition in order to be able to reinstall without loosing all data. But there is no boot partition. The root partition has about 1.3 Gb free space. 

Uname gives me the same kernel as apt-get complains about, namely 2.6.32-31-generic. 

*sudo apt-get clean* gives me nothing but a new line. 
*sudo apt-get update* proceeds and finishes fine
*sudo apt-get upgrade* won't complete as it crashes when installing linux-headers-2.6.32-31-generic.

So no success. What if she boots from an older kernel? Could that solve it?

---

### Post by linuxinstalledfromhdd on 2011-06-09
I would upgrade to the latest kernel at this point:

[http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa)

---

### Post by 1/0 on 2011-06-09
Booting into an older kernel does not resolve anything...

---

### Post by 1/0 on 2011-06-09
> **linuxinstalledfromhdd said:**
> I would upgrade to the latest kernel at this point:

[http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa)

Do you mean manually or by apt-get?

---

### Post by 1/0 on 2011-06-09
dpkg.log (writing it so maybe a type-o):

```

install linux-headers-2.6.32-31-generic <none> 2.6.32-31.61
status half-installed linux-headers-2.6.32-31-generic 2.6.32-31.61
status not installed linux-headers-2.6.32-31-generic <none> 2.6.32-31.61

```

Half installed makes sense as */usr/src/* only contain linux-headers-2.6.32-31 and not linux-headers-2.6.32-31-generic. Maybe more missing but that's something I noticed.

---

