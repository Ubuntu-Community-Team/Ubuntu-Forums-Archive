---
title: "Upgrade from 13.04 to [any] on Nexus 7 2012"
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by Giovanni2052 on 2015-12-02
[SIZE=3]Hello,[/SIZE] I have for you quite a challenge here.
I have a Ubuntu 13.04 that I want to upgrade to more recent releases.
It is running in a Nexus 7 2012 (yes, the tablet).

**I have already tried (NO success) to:**

- Upgrade from Software Update (upgrade to 13.10)

- Upgrade from terminal with:

```
apt-get update
apt-get upgrade
```

- Install any app from Ubuntu Software Center or from terminal


**Other information**

- The device can be erased

- I want to upgrade to be able to use xubuntu

- I installed (Ubuntu) in the first place thanks to [this article]("http://www.noobslab.com/2013/10/review-ubuntu-desktop-on-nexus-7-and.html")

---

### Post by grahammechanical on 2015-12-02
Ubuntu 13.04 & 13.10 have both reached end of life.

 13.04 end of life = 27 January 2014.
13.10 end of life = 17 July 2014.

The repositories of both 13.04 & 13.10 are now closed and have been archived and moved to a different location. That is why you cannot do any of those things.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You can upgrade using the End of Life method but you cannot upgrade Ubuntu into Xubuntu. So, why not do a fresh installation of Xubuntu 15.10 and then at the end of April next year you can upgrade to Xubuntu 16.04.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by Giovanni2052 on 2015-12-05
Hi, thank you for your kind reply. While upgrading to 13.10 from the EOL Upgrage page it happens to appear this error:

> Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
flash-kernel: installing version 3.8.0-35-generic
**Flashing kernel and initramfs to /dev/mmcblk0p2... /dev/mmcblk0p2: updated is too big for the Boot Image (11429888 vs 8388608 bytes)**

failed.
run-parts: /etc/initramfs/post-update.d//flash-kernel exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Errors were encountered while processing:
 initramfs-tools

Upgrade complete 

The upgrade has completed but there were errors during the upgrade 
process. 

To continue please press [ENTER]


---

### Post by Vladlenin5000 on 2015-12-05
As said above, do a fresh install. Mentioning a possibility isn't the same as a recommendation. Post #2 mentions it for sake of truthfulness and completeness only - it would be false stating that you can upgrade that way - not as two equally valid options.

---

### Post by Giovanni2052 on 2015-12-05
Thank you.
I actually have to admit I do not know what you mean as fresh install. Do you mean to install a recent release from zero? In this case, do you know how can I do that in my device? In a normal laptop or computer I would use some USB pen or CD but I have no idea how to do it in my nexus.

---

### Post by Vladlenin5000 on 2015-12-05
Yes, a fresh install is from scratch. But it really isn't an option for you and sorry for not noticing it was a special case.

The instructions you posted are the easy way - via a Noobslab script - but are now obsolete. However, you can try the suggestion in the second comment although it will, at best, get you to the next but also EoL release. You would have to repeat the process again to get to 14.04 LTS. Meanwhile, the potential for errors like the one you're experiencing is huge.

Ubuntu (desktop) was never meant to ARM devices. It's always some sort of 'hack' using the not-really-official ARM port. Not recommended. 
**Ubuntu Touch** is the recommend one: [https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)
Unfortunately for you this is still very limited and there's currently no easy way to install any currently supported desktop release. It has been abandoned a couple of years ago in favor of Touch like it says in the note  [here]("https://wiki.ubuntu.com/Nexus7/Installation").

---

### Post by TYPELiFE on 2016-03-27
Side note, as Vladlenin5000 mentioned there's no upgrade path, but if you still need to apt-get update and apt-get install, you need to update /etc/apt/sources.list:

```
sudo sed -i -e 's/ports.ubuntu.com\/ubuntu-ports/old-releases.ubuntu.com\/ubuntu/g' /etc/apt/sources.list
```

---

