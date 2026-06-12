---
title: "quiet splash and old kernel"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by generalnono19 on 2014-08-08
hello i have problem after updateing intel graphic so after booting the login screen be black screen and u can't do anything so u must reboot the laptop and edit grub useing "nomodeser" and remove "quite splash" to work normal but slowly right now i try to fix this problem but i faild ti fix it so i choose from booting in grub useing old kernel and everything is ok in old kernel so i need who can help me to fix the problem in now kernel or how remove new kenel to stay working in old kernel am using now ubuntu 14.04 LTS.

---

### Post by sudodus on 2014-08-08
Welcome to the Ubuntu Forums :-)

Please ask for details, if you find these instructions too complicated!

-o-

Check what kernels there are for example by looking at the boot directory

```
ls -l /boot
```

You install a kernel like this

```
sudo apt-get install linux-image-  # press tab to get a list of alternatives 'TAB completion'
```

and you remove a kernel like this

```
sudo apt-get remove linux-image-  # press tab to get a list of alternatives 'TAB completion'
```

and then run

```
sudo update-grub
```

***Warning***: do not remove the kernel you are running! Check carefully the version numbers! Boot into the old kernel (make sure it works properly) and then you can remove the newer kernel.

If you *update/upgrade instead of update/dist-upgrade*, you will not upgrade the kernel.

```
sudo apt-get update
sudo apt-get upgrade
```

The GUI tool for upgrading defaults to dist-upgrade and will upgrade the kernel. If that should happen you can always repeat the procedure in this post.

---

### Post by generalnono19 on 2014-08-08
thank u first i start use ubnutu 8.10 :D 
but this problem it's new cuz this first time i use intel graphic maybe problem from my laptop cuz is old i don't know however i have two kernel ok i get this info :

img-3.11.0-26-generic
img-3.13.0-32-generic

am now useing the old 3.11.0-26 and i want remove the new 3.13.0-32 but my q there is any problem if i remove the new ?

---

### Post by generalnono19 on 2014-08-08
i remove it the new kernerl and update the grub and terminal tell me ur menu.lst update it but when i reboot my laptop stay in grub and restart again i edit the grub i found it have the kernel was delete it but i update it befor i reboot but it keep save it :/

---

### Post by sudodus on 2014-08-08
How did you delete the kernel? Did you use the following command or something else?

```
sudo apt-get remove linux-image-3.13.0-32-generic
```

Is there a file **menu.lst**? In that case it means you have an old grub. Do you still have the grub system of 8.10? Are you dual booting 14.04 LTS with 8.10?

---

