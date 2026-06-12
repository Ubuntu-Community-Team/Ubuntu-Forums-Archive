---
title: "Upgrading to 9.10 from 8.04..."
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by maramot on 2010-01-11
I have a couple of questions, which I suspect are very lame, but I'm going to ask them anyway :)

1. After I burn the ISO with Ubuntu 9.10 and restart will the installation wipe out the OS loader which I have configured to allow me to start Windows? I don't want to lose the ability to boot windows. That's not that much of a problem even if it happens because I know how to configure ubuntu's boot loader already. I am just worried that the install could alter the MBR or something, so that windows will not start.

2. I have my /home on the same partition where the ubuntu that's about to be upgraded lies. Stupid, I know but it was my first install, so I didn't know :) There's no chance that I will lose my /home contents during upgrading, right?

---

### Post by slakkie on 2010-01-11
> **maramot said:**
> I have a couple of questions, which I suspect are very lame, but I'm going to ask them anyway :)

1. After I burn the ISO with Ubuntu 9.10 and restart will the installation wipe out the OS loader which I have configured to allow me to start Windows? I don't want to lose the ability to boot windows. That's not that much of a problem even if it happens because I know how to configure ubuntu's boot loader already. I am just worried that the install could alter the MBR or something, so that windows will not start.


Karmic uses grub2 by default, which is different from grub-legacy as used by pre-karmic releases of Ubuntu.

Unless you tell the installer otherwise it will install grub2 on the mbr, but it should be able to see your Windows install and you should be able to start Windows. Could be that you need to run update-grub/grub-update the first time you have booted Ubuntu. Have seen posts where this was needed.

You can say to Ubuntu to install grub on the same disc as your Ubuntu installation. Which means you should chainload from your MBR bootloader to Ubuntu for it too work properly.


> 
2. I have my /home on the same partition where the ubuntu that's about to be upgraded lies. Stupid, I know but it was my first install, so I didn't know :) There's no chance that I will lose my /home contents during upgrading, right?

It will override your /home if you don't have a seperate partition for it. If you have space left on your disk, create a partition and move your /home contents to that disk, then install 9.10 and make sure you don't format the partition which contains your homedir.

I would backup your /home if I was you, install 9.10, create a seperate partition for your /home and mount it accordingly, then restore your backup. Restoring the backup is something I would do with a liveCD or while not running a GUI.

---

### Post by maramot on 2010-01-11
Thanks, slakkie. In that case I'll backup my /home and upgrade, making a new partition for /home. 

I have vague memories that when I bought my laptop I installed ubuntu, and then windows, and I got trapped inside windows, because it had wiped out the MBR and installed only its own loader there. That's why I was unsure about point 1.

---

### Post by slakkie on 2010-01-11
> **maramot said:**
> Thanks, slakkie. In that case I'll backup my /home and upgrade, making a new partition for /home. 

I have vague memories that when I bought my laptop I installed ubuntu, and then windows, and I got trapped inside windows, because it had wiped out the MBR and installed only its own loader there. That's why I was unsure about point 1.

Ahh, yes, Windows is a bitch, it just ignores other operating systems..

---

### Post by SecretCode on 2010-01-11
> **maramot said:**
> I have vague memories that when I bought my laptop I installed ubuntu, and then windows, and I got trapped inside windows, because it had wiped out the MBR and installed only its own loader there.

Windows will always do this. Fortunately you can recover from it: [RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=fullsearch&context=180&value=linkto%3A%22RecoveringUbuntuAfterInstallingWindows%22)

> **slakkie said:**
> Ahh, yes, Windows is a bitch, it just ignores other operating systems..
:nod:

---

### Post by Dale61 on 2010-01-12
Am I correct in thinking you want to upgrade from 8.04 directly to 9.10?  I don't think it can be done without encountering any problems.  You must upgrade one step at a time (8.04 to 8.10 to 9.04 to 9.10) unless you have an LTS version.

---

### Post by slakkie on 2010-01-12
> **Dale61 said:**
> Am I correct in thinking you want to upgrade from 8.04 directly to 9.10?  I don't think it can be done without encountering any problems.  You must upgrade one step at a time (8.04 to 8.10 to 9.04 to 9.10) unless you have an LTS version.

With 8.04 it is possible to upgrade directly to 9.10, it is the one exception that proves the rule :)

---

### Post by Dale61 on 2010-01-12
So it's an LTS version?

6.06 was the same - upgrade direct to 8.04, but LTS to LTS.

---

### Post by slakkie on 2010-01-12
> **Dale61 said:**
> So it's an LTS version?

6.06 was the same - upgrade direct to 8.04, but LTS to LTS.

No, it is a special case since 8.04 is not LTS for KDE users. So Kubuntu made it possible to upgrade from 8.04 to 9.10 directly. You need the latest adept version on 8.04 to do this.

---

