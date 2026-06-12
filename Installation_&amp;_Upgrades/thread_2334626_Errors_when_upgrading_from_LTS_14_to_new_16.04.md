---
title: "Errors when upgrading from LTS 14 to new 16.04"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2016-08-21
Hi, I just upgraded from LTS 14 to LTS 16.04 using software updater, there were several errors and now I see that the kernel being used is 3.13.0-93-generic, shouldnt it be 4 something? I dont know exactly what is wrong with the system, is there a post upgrade script that I can run to see if everything is ok? There were so many errors in the middle that now I am not sure if the system is healthy. I want to post here my dmesg, maybe some good soul can take a look and tell me if there is anything wrong - how do I post the dmesg here? It tells me the attachement is too big :-(

Thanks everyone!!!

---

### Post by howefield on 2016-08-21
Yes, you should be on the 4.4.* kernel if you had successfully upgrade.

What is the output of

```
cat /etc/os-release
```

---

### Post by linux.girl on 2016-08-21
Hi, thank you so much for answering!

The result of the command is;

cat /etc/os-release
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial


I remember that when the upgrade ended it gave me an error that the boot partition was full and it could not restart - can it be that I deleted the correct kernel version from boot partition by mistake? If yes, how do I fix this? The system seems to think it is 16.04

Is there an official ubuntu post upgrade script that checks if everything is ok?

Thanks again!!!

---

### Post by howefield on 2016-08-21
Sounds like you need to delete some old kernels from the /boot to make room for the 16.04.1 kernels. If you were really lucky autoremove would clear some so worth a try,

```
sudo apt autoremove
```

If not, you will have to clear the space manually., what would be the output from..
```
dpkg -l | grep linux
```
```
ls -al /boot
```

---

### Post by linux.girl on 2016-08-22
Hi, I just wanted to tell that the problem is solved by doing 
sudo apt install linux-generic

Thanks everyone!

---

