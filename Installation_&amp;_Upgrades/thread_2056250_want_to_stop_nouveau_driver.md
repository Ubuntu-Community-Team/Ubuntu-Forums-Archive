---
title: "want to stop nouveau driver"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by kedar5 on 2012-09-11
I want to install NVIDIA driver, but I have failed till now.

Following is the thread I followed, but it did not work.
nouveau driver is still running.

[http://ubuntuforums.org/showpost.php?p=10324779&postcount=8](http://ubuntuforums.org/showpost.php?p=10324779&postcount=8)

I am using Ubuntu 10.10.

Thanks for help.

---

### Post by GeForce 9500GT on 2012-09-11
> **kedar5 said:**
> I want to install NVIDIA driver, but I have failed till now.
 
Following is the thread I followed, but it did not work.
nouveau driver is still running.
 
[http://ubuntuforums.org/showpost.php?p=10324779&postcount=8](http://ubuntuforums.org/showpost.php?p=10324779&postcount=8)
 
I am using Ubuntu 10.10.
 
Thanks for help.
 
Blacklisting the nouveau driver is a good thing to do. Before going any further, best to do is adding the [x-swat PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"). Then delete every nvidia-nouveau driver using synaptic. If you did that, close synaptic and open a terminal and execute the following commands:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo nvidia-xconfig
``` 
This will install the correct Nvidia driver. Make sure to follow up the instructions given in the terminal.

---

### Post by Elfy on 2012-09-11
Possibly because you are using an end of life version.

---

### Post by GeForce 9500GT on 2012-09-11
> **Elfy said:**
> Possibly because you are using an end of life version.
 
Yes, version 10.10 is no longer supported. Best is also to upgrade to a newer version.

---

### Post by kedar5 on 2012-09-12
I removed the nouveau driver from my system with the help of following thread.
 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
 
But many thanks for the replies.
 
Regards.

---

