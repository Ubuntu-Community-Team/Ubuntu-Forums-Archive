---
title: "VitualBox not being updated/upgraded"
date: 2024-01-16
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2024-01-16
VituralBox was not working, hence the update.  Below is the result.

```

sudo apt-get update && sudo apt-get dist-upgrade -y
[sudo] password for ron: 
Hit:1 http://ca.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:3 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy-security InRelease
Hit:5 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu jammy InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  systemd-hwe-hwdb virtualbox virtualbox-dkms virtualbox-guest-additions-iso
  virtualbox-guest-utils virtualbox-guest-x11 virtualbox-qt
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```

---

### Post by deadflowr on 2024-01-17
it's currently being phased-updated.
You can run
```
apt policy virtualbox
```
and it'll tell you this
```
virtualbox:
  Installed: (none)
  Candidate: 6.1.48-dfsg-1~ubuntu1.22.04.1
  Version table:
     6.1.48-dfsg-1~ubuntu1.22.04.1 500** (phased 20%)**
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages
     6.1.32-dfsg-1build1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages

```
I've bolded the important part that tells us it has been phased out to 20% of users so far.

---

### Post by SeijiSensei on 2024-01-17
Follow the instructions for "Debian-based" distributions here: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads).

It will add the Oracle repository to your sources. That will keep your installation up-to-date along with the other software on your machine.

---

### Post by Alligator on 2024-01-17
I've installed 7.0.14 and it has halted while installing Windows 10.

---

### Post by Alligator on 2024-01-17
Phased at 100% and the installed and Candidate are the same.

---

### Post by Alligator on 2024-01-17
I've installed the new extension and it all works,  now to figure out how to put SOLVED  in the proper place.

---

### Post by ajgreeny on 2024-01-17
> **Alligator said:**
> I've installed the new extension and it all works,  now to figure out how to put SOLVED  in the proper place.
Go to *Thread Tools* at the top of the thread and choose **Mark this thread as solved** there

---

