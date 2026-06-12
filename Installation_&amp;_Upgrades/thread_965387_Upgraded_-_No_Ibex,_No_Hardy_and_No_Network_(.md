---
title: "Upgraded - No Ibex, No Hardy and No Network :("
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by ajacx on 2008-10-31
So earlier I tried updating from 8.04LTS to 8.10 via network using the update manager. Everything seemed to be going smooth and it deleted all the old packages and asked me to reboot, after which I got stuck at rc.local , right after its finished checking my batteries. So I also have the problems everyone in this thread has - [http://ubuntuforums.org/showthread.php?t=963774](http://ubuntuforums.org/showthread.php?t=963774) -, except I'm still on 8.04! (problem being - in /var/log/Xorg.log vesa and the mouse fail to load, and there is a fatal error: no screens found.)

The trouble is I don't see the new kernels in the grub menu, and I was actually booting the old 2.6.21-24 kernel on 8.04. I can get into recovery mode and when I ls -l /boot I find that I don't have any of the new kernels installed.

So now I don't have the upgrade, I can't boot even from the 8.04 kernels , and I can't get my network working in recovery mode. I have managed to download the alternate CD (via windows) and I'm able to mount it in recovery mode, is there anyway to apply the updates from the CD? (I can't gksu "sh cdrom/cdromupdate" because it doesn't allow it, can't load the GUI) 

If I reboot into the CD and install, does it make a fresh install and wipe the disk? I have two hard disks, one has XP and the other has/had 8.04, and so if I do have to make a clean install then I'd like to transfer all the contents of my home directory to some temporary folder on my windows hard drive, since I don't have an extra machine or storage device handy. I don't know if this is useful, but I do have cygwin installed but I can't see my linux hard drive on it. I'm very new at all of this, and I would be really grateful for any help anyone could lend. 

Can someone please tell me how to make, transfer and store a backup of my home directory now, its about 8-9 GB. Of course if its possible to upgrade and fix these problems without a clean wipe, this would not be necessary, but it would be useful to know.

Thanks

---

### Post by ajacx on 2008-11-01
I just thought of another solution, can I install Intrepid as another partition on my current HD that has the corrupt version of Ubuntu, and then transfer the contents of my home folder to the new installation? I'm really worried about losing all the data in my home directory (I know I should have backed it up *before* the upgrade :( ), so if anybody has any suggestions or recommendations I'd love to hear them.

---

### Post by ajacx on 2008-11-01
Anyone? I'm pretty certain if I get my network working I'd be able to update the and upgrade like everyone else who had this problem. I have a DSL connection and used to start my internet using "pon dsl-provider" but when I type pppoeconf to try setting it up, I get an error saying pppoeconf does not exist. Does anyone know how I can work around this. I've tried dhclient but it doesn't let me logon with my username and password for the dsl connection.

One thing I can confirm is that this is a very minimal upgrade to 8.10, but its really puzzling since I don't have the new kernels.

---

### Post by confused57 on 2008-11-01
> **ajacx said:**
> I just thought of another solution, can I install Intrepid as another partition on my current HD that has the corrupt version of Ubuntu, and then transfer the contents of my home folder to the new installation? I'm really worried about losing all the data in my home directory (I know I should have backed it up *before* the upgrade :( ), so if anybody has any suggestions or recommendations I'd love to hear them.
  This should work, at least to transfer your home data to your new Intrepid install.

  If you're able to boot into Windows on the other hard drive, you could install fs-driver, which will allow XP to access your ext3 filesystems, then you can copy your home data to a folder in Windows.  I'll see if I can find a link to fs-driver.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

