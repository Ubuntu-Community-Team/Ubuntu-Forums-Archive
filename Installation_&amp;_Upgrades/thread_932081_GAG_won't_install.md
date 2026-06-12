---
title: "GAG won't install"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by opensuse on 2008-09-28
when I follow the GAG instructions for UBUNTU I get

```
chris@ubuntu:~$ cd gag4.10
chris@ubuntu:~/gag4.10$ cd linux
chris@ubuntu:~/gag4.10/linux$ sudo gag-install /dev/sda
[sudo] password for chris: 
sudo: unable to execute /sbin/gag-install: No such file or directory
chris@ubuntu:~/gag4.10/linux$ 

```

---

### Post by Herman on 2008-09-28
:)
It looks to me as if you skipped a command.
Try this,
```
chris@ubuntu:~$ cd gag4.10

chris@ubuntu:~/gag4.10$ cd linux

chris@ubuntu:~/gag4.10/linux$ **sudo ./copy-files.sh**

chris@ubuntu:~/gag4.10/linux$ sudo gag-install /dev/sda

[sudo] password for chris: 

GAG installer, v4.10
Language: ENGLISH
Keyboard type: QWERTY
Will install GAG on device /dev/sda
GAG installer, v4.10
Language: ENGLISH
Keyboard type: QWERTY
Will install GAG on device /dev/sda 

GAG successfully installed in /dev/sda

Don't forget to install GRUB in the superblock of your root partition using 

grub-install

chris@ubuntu:~/gag4.10/linux$
```Regards, Herman :)

---

### Post by opensuse on 2008-09-28
Thanks Herman. I had already run the copy-files script and omitted it in my subsequent attempts to install gag. When I ran the script and installed gag in the order that you instructed, it worked. Now I can choose my OS when I boot. Thanks again.

---

