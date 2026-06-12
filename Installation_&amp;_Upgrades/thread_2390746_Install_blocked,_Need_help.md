---
title: "Install blocked, Need help"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by sireangelus on 2018-05-02
Hi, after a series of experiments on an upgraded 18.04 install, i find myself with the need to tell the system that it must NOT try to remove a package. Is there any way to tell the system that this package does not exist or to delete the removal request? Thank you.

---

### Post by dino99 on 2018-05-02
Maybe you're asking to pin a package  [https://askubuntu.com/questions/663572/how-to-pin-a-ppa-package/663688](https://askubuntu.com/questions/663572/how-to-pin-a-ppa-package/663688)

---

### Post by sireangelus on 2018-05-02
> **dino99 said:**
> Maybe you're asking to pin a package  [https://askubuntu.com/questions/663572/how-to-pin-a-ppa-package/663688](https://askubuntu.com/questions/663572/how-to-pin-a-ppa-package/663688)
 i'll thank you for your time ,but your answer is completely out of topic.

---

### Post by tinylagarto on 2018-05-02
What package if we might ask?

---

### Post by QIII on 2018-05-02
Also, what was the nature of your experiments?  Understanding the current state of your machine is critical to our ability to assist.

---

### Post by sireangelus on 2018-05-06
ok, i was experimenting with git zfs, and a series of uninstalls and bad decisions made left me withouth initramfs-tools. So, when linux-image-extras XXXX tries to be removed, it gets stuck beacuse can't find initramfs. Can't install initramfs because first it wants to remove the packages marked for removal. Now, even though this information is completely unecessary since i asked a question as "how do i do this", can someone please help me tell the system to unmark the package for deletion or that the package does not exist in the first place so that there is no need for removal? Thank you.

---

### Post by tinylagarto on 2018-05-06
Not sure about your experiments.
I would try from terminal:

```
 sudo apt update
```

Post any unusual output here. 

It seems to be a problem with the package system and you have to fix this first.

---

### Post by sireangelus on 2018-05-08
thank you for your kind assesment, but i am asking a simple question: i have a package that is marked for removal. I want the system to ignore the existence of that package. How do i do that? I am not trying to diagnose the problem , i just need a functional piece of code, script, series of cli commands to do this. thank you.

---

### Post by sireangelus on 2018-05-10
Up

---

### Post by sireangelus on 2018-05-13
Up

---

### Post by Impavidus on 2018-05-13
It sounds like your system is well messed-up already and without knowing the details I can't say whether this will help to fix it or make matters even worse. But let's try something and you may learn more about the internals of the system. If it doesn't work, you can always try a fresh install.

Why is the package manager trying to remove linux-image-extra-...? Is it marked for removal and currently installed, then marking it for install may work. Just use apt-get install or dselect or synaptic, whatever is installed on your computer. If it is to be removed because of some package conflict, or currently partially installed, that won't work. You'd be hacking your way through the databases used by package management and probably make matters worse. You can use ```
dpkg -l linux-image*
```to find the current status of the package.

But the way to solve your problem is probably something completely different. Use ```
sudo dpkg -i <package.deb>
``` to reinstall initramfs-tools. You may also have to reinstall initramfs-tools-core or initramfs-tools-bin. You may be able to use ```
apt-get download <package>
``` to get the .deb files. Read the manual pages for more details:```
man <tool>
```dpkg can install and remove packages, disregarding inconsistencies in package management (as long as all tools necessary for the operation are installed), and therefore can be a useful tool to fix package management when it is rather badly broken.

---

### Post by sireangelus on 2018-05-23
i cannot install anything related to linux-* because i'm missing initramfs-tools, so every time it tries to mess with kernel stuff the script fails. i'll try and  do it your way though, your proposal is interesting. Thank you for your help

---

### Post by sireangelus on 2018-05-27
You set me on the right track! you gave me the tools that i needed to solve my problem! Turns out that there was a script into initramfs-tools that tried to do something to a zvol, crashing. Deleting the script and using your instruction to fix the dependencies fixed this problem. Thank you!

---

