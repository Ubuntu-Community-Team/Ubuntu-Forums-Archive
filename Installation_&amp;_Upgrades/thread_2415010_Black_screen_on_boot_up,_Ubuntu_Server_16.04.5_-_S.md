---
title: "Black screen on boot up, Ubuntu Server 16.04.5 - Server has no graphics card"
date: 2019-03-18
forum: Installation &amp; Upgrades
---

### Post by ronan25 on 2019-03-18
I have searched this forum and search engines for answers, and tried many, but no joy.
I had a corrupt system, Ubuntu 16.04.5 (yes it is server).

The system became corrupt when someone ran a ```
chmod 777
``` command for etc/ folder,  
I ran rescue broken system a few times, checked files and so forth, to no avail. I was never able to get it to boot. I just got the black screen and no further. I checked files etc, but still never got past the back screen.
I ended up without a fix, and I made a backup of the etc/ directory (as through rescue a broken system I could get command line). I then proceeded to reinstall 16.04.5
However, on reinstalling I reformatted the HD, and reinstalled, yet when I go to boot up I have black screen.

There is no graphics card with this server, and in the instaliation file called syslinux.cfg I amended the file code to read for example:
```
label ubnentry6
          menu label ^Install Ubuntu Server
          kernel /install/vmlinuz
          append initrd=/install/initrd.gz file=/cdrom/preseed/ubuntu-server.seed vga=off console=ttyS0,115200n8 –
```
 
In Grub, I have replaced ‘Quiet Splash’ with ‘Quiet Splash nomodest ‘  and ‘nomodest’   and also tried ‘text’ but again no joy. I did run sudo update-grub
Anybody else have any ideas on how to get past this black screen? I imagine it is still looking for a graphics card of some sort, but as said it is a straight server with no graphics as all on it.

---

