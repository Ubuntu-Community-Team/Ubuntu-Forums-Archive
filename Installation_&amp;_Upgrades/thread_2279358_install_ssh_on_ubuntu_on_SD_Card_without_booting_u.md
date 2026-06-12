---
title: "install ssh on ubuntu on SD Card without booting ubuntu"
date: 2015-05-22
forum: Installation &amp; Upgrades
---

### Post by Kapil_Yadav on 2015-05-22
Hi,

I burned ubuntu image on SD Card so that I can use it on my raspberry pi 2. But since I dont have hdmi display and sshserver is not preinstalled on ubuntu, I have no way of accessing my raspberry pi. ssh doesnt work because sshserver is not installed on ubuntu running on raspberyr pi. I am following this [link]("https://wiki.ubuntu.com/ARM/RaspberryPi") for installing ubuntu on raspberry pi.

What can I do to run ubuntu on raspberry pi headless???

Thanks

---

### Post by sandyd on 2015-05-22
1. Locate partition of raspberry pi root partition on SD card
```

sudo fdisk -l
```

The command will show all disks/cards/storage devices and the partitions on each.

2. Create a mount point and mount the root partition
```

sudo mkdir /mnt/RPI
sudo mount *partition* /mnt/RPI

```
Replace *partition* with the partition (starting with /dev/)

3. Copy over resolv.conf to enable internet
```
sudo cp /etc/resolv.conf /mnt/RPI/etc/resolv.conf
```

4. Chroot into install
```

sudo chroot /mnt/RPI
```

5. Install stuff
```

sudo apt-get install openssh-server
```

6. Exit chroot
```

exit
```

---

### Post by Kapil_Yadav on 2015-05-23
Hi Sandyd,

Elegant solution.. :)

Thought I got suck at chroot command. It is showing this error 

failed to run command &#8216;/bin/bash&#8217;: Exec format error

When I searched on internet, I found out that it was because I am using 64-bit ubuntu on my laptop and OS that I installed on SD Card was 32-bit. Looks like I have to find a laptop running 32-bit ubuntu to make my way through.

---

### Post by Kapil_Yadav on 2015-05-23
I put a line "apt-get install openssh-server" in rc.local at /etc. Then I put the sd card in the raspbery pi. 
But that didnt work.. :( . I dont know the reason.

---

### Post by tgalati4 on 2015-05-23
It's possible that *openssh-server* requires several dependencies (packages) that need to be installed.  That would require an interactive "yes" response before *apt-get* will install those packages.  You can use the -y switch to answer "yes" automatically.  It might be easier to find a TV and use the composite out on the RaspberryPi so you can see what is going on.

---

