---
title: "grub fails because of fakeraid"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by krazykanuk on 2010-02-13
I originally posted this [http://ubuntuforums.org/showthread.php?t=1405933](http://ubuntuforums.org/showthread.php?t=1405933) but I now know the problem. Grub fails when it goes to install because of the fakeraid. I have tried to follow the how-to located here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) but I get to Step 5 and it fails with the error 
```

sudo chroot /mnt/root /bin/bash
bash: groups: command not found

```This will be installed on a system where ubuntu 9.10 will be the only operating system right now there is 2 320GB SATA hard drives with possibility of a third in the near future. the second drive has all the backups from my old Linux stuff (Slackware) and drive shares that I share with Windows machines as well as the old /home directories, so this drive I don't want touched by the install (but this drive is showing up how I expected /dev/sdb), the first drive (which is showing up as /dev/mapper/nvidia_fgjhebae) is the one I am partitioning and formatting to put ubuntu onto. It fails on the grub portion and then it putting me into ubuntu using a livecd that why everything slow and so on. So how do I get past this error the fakeraid is giving me and how much did I not get installed because it stopped at 94%. This is new to me because when I install Slackware I partition it and then it recognizes the /dev/sda and /dev/sdb with no extra effort.

---

### Post by darkod on 2010-02-13
Are you using the Alternate Install CD image? For raid and/or lvm you need to use alternate install cd.
Just scroll down:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by krazykanuk on 2010-02-13
No, I wasn't I was using the CD created from the ubuntu-9.10-desktop-amd64.iso disk image downloading the ubuntu-9.10.alternate-amd64.iso now I will try it again once it finishes downloading and I burn it to CD.

---

### Post by krazykanuk on 2010-02-13
This going to have to wait until I get more disks, I have gone through 3 disks trying this so far (ubuntu-9.10-desktop-amd64.iso, ubuntu-9.10-server-amd64.iso and ubuntu-910-alternate-amd64.iso) and now I need a fourth. It finished downloading I put it on CD I booted to the CD and started the install and it fails and won't install the base system fails on zlib1g_1.2.3.3.dfsg-13ubuntu3_amd64.deb and then something about bootstrap. I reboot select to check the disk for defects and it fails on /pool/yelp_2.28.0-ubuntu2_amd64.deb (14%) and then reboots when I select continue. I will have to put something else on until I can get more disks, for I cant have this system down for that long.

---

