---
title: "installing mutiple ubuntu on pc"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by alex374 on 2015-04-30
Hello,

I need to install two ubuntu systems which are same version (12.04 ) on my pc. I already have one installed on the hard disk. 

Firstly, is it ok to install two same version ubuntu system by partitioning. Will there be any conflict in finding both of them when the system starts.

I plan to use both OS's for different applications and therefore need help regarding this.

The trouble is, how do I deal with swap when installing the second one? Some posts suggested that I can use the same swap area. Also, when booting will the two ubuntu OS show up properly and how will I know which is which as both are same version OS.

Any help will be deeply appreciated.

Thanks

Alex

---

### Post by Elfy on 2015-04-30
Yes you can do it.

Yes you only need one swap.

How you tell the difference is up to you, but when you've booted one - the other will just be a partition in your file manager. You won't be booting both at the same time.

Lastly - any reason why you're installing the *old* LTS, 14.04 is an LTS too.

---

### Post by alex374 on 2015-04-30
Hi,

Thanks for your quick reply. I actually use it for my research using the ROS(Robot Operating System). The 12.04 version is supported for one of the ROS release and does not install on 14.04. I have really messed up codes that I need to arrange in the new partition keeping the previous one intact ( Do not break it if its already working.. ;)), so need a new partition with Ubuntu. 

Thanks for the answer though. I will try it tonight. Oh, and by any chance do you a way to clone my ubuntu drive for a backup? 

Alex

---

### Post by Elfy on 2015-04-30
[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

I don't do that here so no experience of such. My installs rarely last longer than 3 months.

---

### Post by CantankRus on 2015-04-30
During the second install process choose to install grub to the partition used (eg /dev/sda**5**) instead of the usual  drive (eg /dev/sda).
That will allow you to keep using grub from your original install when and if you uninstall the second install.
You need to then log in to your first install and run....
```
sudo update-grub
``` 
for your second install to be found and added to the grub menu.

---

### Post by alex374 on 2015-04-30
Hi,

Ok great!. This will be helpful for finding both OS's when starting grub. Many thanks.

Alex

---

