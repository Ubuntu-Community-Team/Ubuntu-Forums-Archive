---
title: "can't install tinyproxy"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by daytripper1021 on 2010-03-05
Another newbie here trying out Ubuntu 9.10 Linux. :)
 
I would like to install tinyproxy so I downloaded the package from the 'net. However, when I tried to install this is what happened:
 
[EMAIL="root@RPBox:~/tinyproxy-1.8.0"]root@RPBox:~/tinyproxy-1.8.0[/EMAIL]#  sudo apt-get install tinyproxy
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package tinyproxy

It seems that since Ubuntu was installed on my server via CD, apt-get is always searching for the package there. But the problem is that the CD is not anymore in the server and that the server itself is on a remote site.
 
Is there a way to tell apt-get that "hey! I don't have the CD anymore so install this package that I downloaded, ok?!"?
 
Hope you can help.
 
Thanks.

---

### Post by Soulcage on 2010-03-05
You can't use apt-get to install something you downloaded off a site.
It downloads and then installs a package, you would need to read the readme or install file inside the folder for tinyproxy.

If you want to use apt-get you should try:
sudo apt-get update
sudo apt-get install tinyproxy

---

### Post by daytripper1021 on 2010-03-05
> **Soulcage said:**
> You can't use apt-get to install something you downloaded off a site.
It downloads and then installs a package, you would need to read the readme or install file inside the folder for tinyproxy.
 
If you want to use apt-get you should try:
sudo apt-get update
sudo apt-get install tinyproxy
 
Thanks. I forgot to mention that I did read the install file and it told me to run ./configure. However, upon running it, I ran into [this problem]("http://ubuntuforums.org/showthread.php?t=1422150").

---

### Post by Soulcage on 2010-03-06
Well since your ubuntu install doesn't have a internet connection you best bet is to just go to [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=tinyproxy]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=tinyproxy") and download the package there and make sure to get any dependencies it wants too.

---

