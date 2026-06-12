---
title: "how to dual boot ubuntu and slackware"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by ikkem on 2007-10-15
Hi all
I wanted to ask how to dual boot ubuntu and slackware with grub I have been running ubuntu for almost a year now....
I made partitions and installed slackware on the second partition the root directory is installed on hda3 and the swap is on hda4....
The output of sudo fdisk  -l is:
>  Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         851     6835626   83  Linux
/dev/hda2             852        4990    33246517+   5  Extended
/dev/hda3            4991        9776    38443545   83  Linux
/dev/hda4            9777        9964     1510110   82  Linux swap / Solaris
/dev/hda5             852        1039     1510078+  82  Linux swap / Solaris
/dev/hda6            1040        4990    31736376   83  Linux
 
Thanks in advance....:)

---

### Post by celettu on 2007-10-15
Add a Slackware entry to your /boot/grub/menu.lst

It should look like this:

title Slackware 12
root (hd0,2)
kernel /boot/**vmlinuz-huge-2.6.21.5** root=/dev/hda3 ro
boot

What I put in bold may differ on your system, depending on the kernel you have installed. Check if the version number of "vmlinuz" is the right one.

---

### Post by maybeway36 on 2007-10-15
Most distros have a symlink that points to whatever kernel is newest, which helps with dual-booting. For example, in Debian deriatives it is /vmlinuz and /initrd.gz.

---

### Post by tubasoldier on 2007-10-15
What celettu told you is correct and the "proper" way to do things.

However, you can also chainload grub. Basically you install grub for slackware on to hda3. Then you add a Windows style entry to your Ubuntu installation of grub and point it to hda3. Then when you select it the Slackware grub will start. 

It is a bit reduntant but if you are changing distributions a lot to mess around or play with them then it is a smart way to go because you wont be updating your menu.lst file all the time.

---

### Post by ikkem on 2007-10-15
@celettu/thanks for your quick reaction I got Slackware running now I can start to tweak Slackware also....

@maybeway36 & tubasoldier also thanks for the info..

I guess this thread is solved \\:D/

---

