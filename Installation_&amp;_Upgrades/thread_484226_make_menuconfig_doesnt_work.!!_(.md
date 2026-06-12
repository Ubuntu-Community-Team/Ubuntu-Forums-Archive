---
title: "make menuconfig doesnt work.!! :("
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by i.nihilist on 2007-06-25
Hi..
I have recently downloaded the latest kernel version from kernel.org and tried to install it on my Ubuntu 7.04 fiesty frawn linux. 
What i did was...
-> I have unzipped the .gz file and changed the name of the resulting folder to linux
->Copied this folder named *'linux'* in the */'usr/src* directory
-> now when i **cd** to* /usr/src/linux* directory and then type *sudo make menuconfig *at the prompt, its giving me umpteen no of error messages..! Why is it. 
Is something wrong

---

### Post by 5-HT on 2007-06-25
Do you have all the required build dependencies satisfied? [http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread)
If you're doing a menuconfig, you can ignore: [SIZE=2]libqt3-headers libqt3-mt-dev[/SIZE]

BTW: It's probably best, but contestable, to only symlink the kernel source to /usr/src/linux and to leave the kernel source folder name untouched.

---

