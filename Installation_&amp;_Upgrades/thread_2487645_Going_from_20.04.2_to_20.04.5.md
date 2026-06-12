---
title: "Going from 20.04.2 to 20.04.5?"
date: 2023-06-11
forum: Installation &amp; Upgrades
---

### Post by impy101 on 2023-06-11
I am currently on 20.04.2 and I want to go to version 20.04.5 but when I do apt update and apt upgrade it's not doing anything.

Is there a guide on how I can go to 20.04.5?

---

### Post by Rex Bouwense on 2023-06-11
Welcome to the Ubuntu forums.  If you have Ubuntu 20.04.2 installed, the command to to update your system is: 
sudo apt update && sudo apt upgrade
You will be asked for your password.
To update your computer you must be (at least for a short period of time) a super user.

---

### Post by TheFu on 2023-06-11
Try **sudo apt full-upgrade**

From the manpage:
```

       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove currently
           installed packages if this is needed to upgrade the system as a whole.
```
Don't worry, this will NOT take the system to a different release.

But, it will take you to 20.04.6, which is the current version of the 20.04.x line.
```
$ lsb_release -d
Description:    Ubuntu 20.04.6 LTS

```

20.04.5 is unsupported at this point.  Ubuntu only supports the original 20.04.{nothing} kernel and the latest "dot release" 20.04.6 kernel.  Support for the middle-HWE kernels (20.04.1, .2 .3 .4 .5) was dropped a few years ago. It had ramifications Canonical learned were just too hard to keep maintaining.

If the full-upgrade doesn't get to .6, then install the HWE kernel package following these instructions: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by impy101 on 2023-06-11
> **TheFu said:**
> Try **sudo apt full-upgrade**

From the manpage:
```

       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove currently
           installed packages if this is needed to upgrade the system as a whole.
```
Don't worry, this will NOT take the system to a different release.

But, it will take you to 20.04.6, which is the current version of the 20.04.x line.
```
$ lsb_release -d
Description:    Ubuntu 20.04.6 LTS

```

20.04.5 is unsupported at this point.  Ubuntu only supports the original 20.04.{nothing} kernel and the latest "dot release" 20.04.6 kernel.  Support for the middle-HWE kernels (20.04.1, .2 .3 .4 .5) was dropped a few years ago. It had ramifications Canonical learned were just too hard to keep maintaining.

If the full-upgrade doesn't get to .6, then install the HWE kernel package following these instructions: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I did that as root, but I'm still on 20.04.2

---

### Post by deadflowr on 2023-06-11
What does
```
apt policy base-files
```show?

---

### Post by impy101 on 2023-06-11
> **deadflowr said:**
> What does
```
apt policy base-files
```show?


base-files:
  Installed: 12ubuntu4.3
  Candidate: 12ubuntu4.3
  Version table:
 *** 12ubuntu4.3 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     12ubuntu4 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
     11ubuntu5.7 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
     11ubuntu5 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/main amd64 Packages

---

### Post by deadflowr on 2023-06-11
Are you sure it doesn't say you are on 22.04.2?
The version you have installed is for 22.04.2.

---

### Post by TheFu on 2023-06-12
20.04.6 returns this:
```
$ apt policy base-files
base-files:
  Installed: 11ubuntu5.7
  Candidate: 11ubuntu5.7
```

Details matter.  Run **lsb_release -d** to see what APT thinks you have installed.

---

