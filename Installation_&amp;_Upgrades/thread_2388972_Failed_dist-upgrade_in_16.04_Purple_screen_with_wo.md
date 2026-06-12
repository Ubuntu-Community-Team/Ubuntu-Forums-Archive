---
title: "Failed dist-upgrade in 16.04: Purple screen with word Ubuntu and dots below"
date: 2018-04-09
forum: Installation &amp; Upgrades
---

### Post by nottaken2 on 2018-04-09
From within Ubuntu 16.04, although all prior **dist-upgrade **succeeded, following commands result in a purple screen with word Ubuntu and dots below:

 
 ```
$ sudo apt-get update
$ sudo apt-get upgrade
$ ls -laFt /boot
$ df -h
$ sudo apt-get dist-upgrade
$ sudo  apt-get update
$ sudo apt-get dist-upgrade
$ df -h
$ sudo apt autoremove
$ df -h
$ ls /boot
$ ls -laFt /boot
$ sudo apt-get update
$ nvidia-smi
$ sudo apt-get upgrade
$ nvidia-smi
$ sudo shutdown -P now
```

Full console log is attached. 

Menus that come up during the boot-process:

```
A. GRUB Options:
   a. Ubuntu
   b. Advanced options for Ubuntu
   c. System setup
B. After (A.b), options are:
   a. Ubuntu, with Linux 4.13.0-38-generic
   b. Ubuntu, with Linux 4.13.0-38-generic (upstart)
   c. Ubuntu, with Linux 4.13.0-38-generic (recovery mode)
   d. Ubuntu, with Linux 4.13.0-36-generic
   e. Ubuntu, with Linux 4.13.0-36-generic (upstart)
   f. Ubuntu, with Linux 4.13.0-36-generic (recovery mode)
C) After selecting (B.a) or (B.d):
   a. Prompt to decrypt hard-drive – password is accepted
D) Then just see a purple screen with “Ubuntu” and dots below Ubuntu.

``` 


Am able to boot from a live USB stick and look at the encrypted hard-drive [as per instructions here]("https://askubuntu.com/questions/653408/mounting-encrypted-luks-partition-from-live-cd") – so have access to logs on the system.

Please advice.

---

### Post by turb03 on 2018-04-10
Hello there,
I am not really a professional programmer with ubuntu, but I have an idea that my fix your error. Turn on your machine and hold down shift button to enter the grub menu. After you enter it, go to advance mode and then click **'e'** the edit it. Search for where it says **'quiet splash'** and add **'nomodeset'** after it and then click *Control + X *to save the code and boot the system with the updated code.

I am not sure if that is going to work, but I had a similar issue and that fixed it for me. See if it works and tell me if it fixed it or it is still the same. Hope you get it working :)

- turb0

---

