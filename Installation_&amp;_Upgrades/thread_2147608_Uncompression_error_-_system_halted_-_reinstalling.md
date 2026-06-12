---
title: "Uncompression error - system halted - reinstalling kernel and grub"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by darekch on 2013-05-22
I have lubuntu 13.04. Few days ago I upgraded my kernel up to 3.8.0.21.37. After that at reboot I was hit by "uncompression error - system halted". Message appears right after "loading initrd". After that I try to do repair by myself. I started livecd, chroot to my system, then reinstall kernel (apt-get purge/install linux-image), update-initrams -u -k all and I reinstall grub but all that didn't solve my problem. I have no more idea what's wrong.
To be more precisely I have grub on my flashdisc and all my system on the hard drive. That configuration has been working for me for month now and I previously updated kernel without any problem.
Oh, there was one issue. Upgrading kernel up to 3.8.0.21.37 I hit ouf of space. Thus I removed older kernel and reinstalled new kernel once more. I guess this could be the cause of my troubles.

---

### Post by darekch on 2013-05-22
I also did memtest of my RAM which is perfectly ok.

---

### Post by darekch on 2013-05-23
I think I know what's the cause of my problem. During boot grub doesn't see my hdd. The problem is that the live cd does see my drive and I can perfectly mount and use the drive. So it seems that my drive is OK. I say grub doesn't see my drive because I don't see the drive in busybox (which appears few minutes after unsuccessful boot). Now under this busybox I can't find my hard drive in /dev/ or in /dev/disk/by-uuid/. In both directories I see only my 2 flash drives (one with grub for boot, other with live cd). Thus I can't even boot from busybox. Anybody has an idea what's wrong?

---

### Post by darekch on 2013-05-24
Ok, I've managed to help myself. It took 3 long evenings, but at the end I fix it. Unfortunetly I can't describe verbose fix description as trying to fix the problem I go through too many cases. However I will describe process that helped me - reinstalling kernel + grub.

!!! Below instructions are rather for average linux users. I thought that to fix my system I need to completly remove /boot directory! IF YOU ARE BEGINNER YOU DON'T WANT TO DO THAT!!! I make this decision as apt was reinstalling kernels without failure but my system couldn't boot.

**Preparations**
[LIST=1]
[*]Grab live cd with same architecture as Your system you will rescue (32- or 64- bit). 
[*]Run live cd. Chroot from live cd into your system you will rescue (read [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) for info how to chroot). All next steps are described in the context of root@chroot-system-to-rescue. 
[/LIST]
**Uninstalling kernels and grub**
[LIST=1]
[*]cd /boot; ls -l 
[*]for all listed kernels try to uninstall them:
```
apt-get -V purge linux-headers-w.x.y-z-generic linux-image-w.x.y-z-generic
``` 
[*]If you won't be able to uninstall kernel due to some post script error, try cleaning apt (see right below) 
[*]Now uninstall grub ```
apt-get -V purge grub-pc grub-common
``` 
[*]```
ls /boot
``` and see what's else there. Uninstall any other kernel you see in /boot. Oh! I see memtest.bin. Let's uninstall it too. ```
apt-get -V purge memtest86+
``` 
[*]check /boot, no files should be there, only /grub and some /extlinux. If there are some other kernels go ahead and uninstall them. Now as everything was uninstalled and /boot is nearly empty, remove directories within boot ```
rm -rf /boot/*
``` 
[/LIST]

**Clean apt if you can't uinstall kernel**
Installing new kernel I got Out of space error - my boot partiton was too small. This caused that I got partially installed kernel which I could not uninstall or install as there was some failure in post-installation scripts. Working solution for such situation is to clean apt and manually remove kernel related files from /boot
```
apt-get clean
rm /var/lib/apt/lists/*
rm /var/lib/apt/lists/partial/*
apt-get clean
apt-get update

``` 
Now try uninstall kernel You couldn't uninstall previously - apt should tell you it's not installed so go to /boot and remove kernel's related files


**Install kernels and grub**
```

apt-get update
apt-get dist-upgrade
apt-get install -V memtest86+  # I think that one 2.8.0-* kernel's post installation procedures were failing if memtest86+ wasn't exist (at least in lubuntu)
apt-get install -V linux-image
apt-get install -V grub-pc grub-common
# NOTE installing grub. Some text-wizard window will appear. Now in most cases You want to install grub on disk's MBR and not in partions so in most cases you would like to choose in that dialog disk like /dev/sdX and not partition like: /dev/sdX[DIGIT]

```

Check /boot now. It was empty, now it's home of various files. In my /boot I have:
```

abi-3.8.0-22-generic
config-3.8.0-22-generic
extlinux
grub
initrd.img-3.8.0-22-generic
memtest86+.bin
memtest86+_multiboot.bin
System.map-3.8.0-22-generic
vmlinuz-3.8.0-22-generic

```

If you have similar files then this store have to end with success. Reboot and keep your fingers crossed.

---

