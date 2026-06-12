---
title: "Deleted Linux headers"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by mykelmykel on 2010-02-07
Please help. I went to Synaptic and mistakenly deleted by Linux-Headers. I'm on a dualboot. Grub only gives me the option now to select Windows. I can't select Linux 9.10 anymore. Please help!

---

### Post by mushwars on 2010-02-07
Are you sure you deleted the headers and not the kernel source?

In any case do this:

1. boot the live cd and choose"try it with no change to my computer"
2. open up a terminal and type this:

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
apt-cache search kernel headers
sudo apt-get install kernel-headers-2.6.31.X <-- the X is what version of the kernel you are booting
sudo update-grub
reboot
```good luck.

[s]I will quick check on a debian machine what the package is called and will edit this post.[/s]

---

### Post by falconindy on 2010-02-07
Chances are this cascaded and deleted the kernel-image as well. Simply reinstalling headers will not solve your problem, as they are unnecessary for day to day operations (unless your day to day includes compiling modules).

---

### Post by mushwars on 2010-02-07
> **mushwars said:**
> Are you sure you deleted the headers and not the kernel source?
yea, only in ubuntu its not source.  Basically do the same steps I listed above but for the actual kernel-image

---

### Post by mykelmykel on 2010-02-07
> **mushwars said:**
> Are you sure you deleted the headers and not the kernel source?

In any case do this:

1. boot the live cd and choose"try it with no change to my computer"
2. open up a terminal and type this:

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
apt-cache search kernel headers
sudo apt-get install kernel-headers-2.6.31.X <-- the X is what version of the kernel you are booting
sudo update-grub
reboot
```good luck.

[s]I will quick check on a debian machine what the package is called and will edit this post.[/s]

Thanks, I'm about to try this. But was wondering what numbers to put in the X. I'd updated as was offered by Update Manager and was trying to remove the older kernel headers whent his happened. I think I deleted the kernel image as well. Would your guide here help out as well, if that is the case? 
Thanks so much for your help!

---

### Post by mushwars on 2010-02-07
> **mykelmykel said:**
> Thanks, I'm about to try this. But was wondering what numbers to put in the X. I'd updated as was offered by Update Manager and was trying to remove the older kernel headers whent his happened. I think I deleted the kernel image as well. Would your guide here help out as well, if that is the case? 
Thanks so much for your help!
The X is teh version of the kernel that you are using. If you are currently booting the .17 kernel (most likely) then you put that in place of the X but you want the kernel-image now and not the kernel headers.

---

### Post by mykelmykel on 2010-02-07
> **mushwars said:**
> The X is teh version of the kernel that you are using. If you are currently booting the .17 kernel (most likely) then you put that in place of the X but you want the kernel-image now and not the kernel headers.

Would following your directions give me the Kernel image?

---

### Post by mykelmykel on 2010-02-07
> **mushwars said:**
> Are you sure you deleted the headers and not the kernel source?

In any case do this:

1. boot the live cd and choose"try it with no change to my computer"
2. open up a terminal and type this:

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
apt-cache search kernel headers
sudo apt-get install kernel-headers-2.6.31.X <-- the X is what version of the kernel you are booting
sudo update-grub
reboot
```good luck.

[s]I will quick check on a debian machine what the package is called and will edit this post.[/s]

When I enter this in terminal: "sudo mount /dev/sda1 /mnt/ubuntu", I get "fuse: failed to access mountpoint mnt/ubuntu: No such file or directory"
Any help....

---

### Post by mushwars on 2010-02-07
> **mykelmykel said:**
> When I enter this in terminal: "sudo mount /dev/sda1 /mnt/ubuntu", I get "fuse: failed to access mountpoint mnt/ubuntu: No such file or directory"
Any help....

read the line right above that you cant just skip steps
sudo mkdir /mnt/ubuntu

---

### Post by mykelmykel on 2010-02-07
I've gone past that error..the new error now is this:
sudo chroot /mnt/ubuntu
chroot: cannot run command `/bin/bash': No such file or directory

---

### Post by mushwars on 2010-02-07
:O you deleted more then your kernel then :O


open another terminal and do this

```
sudo cp /bin/bash /mnt/ubuntu/bin/bash
```


then back in the terminal that you got the error run bash by doing this

```
/bin/bash
```

this will get you out of shell and you can now run inside your system.

---

### Post by mykelmykel on 2010-02-09
> **mushwars said:**
> :O you deleted more then your kernel then :O


open another terminal and do this

```
sudo cp /bin/bash /mnt/ubuntu/bin/bash
```


then back in the terminal that you got the error run bash by doing this

```
/bin/bash
```

this will get you out of shell and you can now run inside your system.

This is the output I get now:
root@ubuntu:/# sudo apt-get install linux-image-2.6.31-19-386
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  wireless-crda
Suggested packages:
  fdutils linux-doc-2.6.31 linux-source-2.6.31
The following NEW packages will be installed:
  linux-image-2.6.31-19-386 wireless-crda
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.8MB of archives.
After this operation, 90.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main wireless-crda 1.10
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-image-2.6.31-19-386 2.6.31-19.56
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main linux-image-2.6.31-19-386 2.6.31-19.56
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.10_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-19-386_2.6.31-19.56_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-19-386_2.6.31-19.56_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

And for the headers, I get this:
root@ubuntu:/# sudo apt-get install linux-headers-2.6.31-19
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-19 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

