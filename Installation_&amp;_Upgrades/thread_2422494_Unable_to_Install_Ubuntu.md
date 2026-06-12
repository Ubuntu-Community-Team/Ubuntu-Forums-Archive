---
title: "Unable to Install Ubuntu"
date: 2019-07-08
forum: Installation &amp; Upgrades
---

### Post by ken-wire1253 on 2019-07-08
Newbie on a Windows 10 Dell laptop that I partitioned into 2 large drives (C:, E:, not yet dual bootable), activated WSL, downloaded Ubuntu 16.04 LTS from Windows Store, and ran it as an executable application (not copied to a USB). Added apt files, Kbuntu and Ubuntu desktops and sddm desktop manager, and updated them. The terminal command line seems to seems to work.  I am unable to install either the Kubuntu desktop or the default Ubuntu desktop.  This error message:

sudo apt-get install ubuntu desk-top
Reading package lists...done
Building dependency tree
Reading state information...done
ubuntu desktop is already the newest version (1.361.3)
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  unity-scope-gdrive : Dependencies: account-plugin-google but it is not going to be installed
E: Unmet dependencies.  Try 'apt-get -f install' with no packages (or specify a solution).

Comments:
1. I tried 'apt-get install' followed by a return key and also followed by 'ubuntu-desktop'  No luck.
2. I tried installing the Kubuntu desktop without success.  I prefer that because I read that it may be easier for a beginner.  I am interested in installing Skrooge and that is a KDE application; it might run easier on a KDE desktop.
3.  I prefer dual boot using C: and E: but that was not offered on my install from Ubuntu 16.04 LTS on the C: drive
4. Thank you in advance!

---

### Post by oldfred on 2019-07-09
It is my understanding that WSL is a terminal only version of Ubuntu.
If you want a full install, you can do a dual boot or a VM - virtual memory install.

But to install Ubuntu, you have to directly boot install media in UEFI boot mode from USB flash drive or DVD. 

Full installs of Ubuntu must use Linux formats like ext4, not Windows formats like NTFS which do not support owership & permissions which provide more protection to system.

See link in my signature below for many links on install instructions and steps required to install.

Dell typically also requires UEFI update from Dell & if SSD a firmware update for SSD. You also need to change drive setting from RAID or Intel RST to AHCI. And first install AHCI drivers into Windows.
Only use Windows to change NTFS partitions & reboot immediately so it can run chkdsk. Make sure Windows fast start up is off, and usually better to have UEFI fast boot off also.

Test Ubuntu live installer in live mode, before actually installing.
       Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by ken-wire1253 on 2019-07-09
This works oldfred and Thank You very much

---

### Post by oldfred on 2019-07-09
Glad it worked. Please change to Solved, so others can find thread.

If you had to do anything slightly different post above or new reply. 
Also may be good to mention Dell model and video, so others with similar Dell can use this thread.

---

