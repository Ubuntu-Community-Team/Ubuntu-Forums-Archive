---
title: "Computer got rebooted during upgrade"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by raunhar on 2010-12-27
While updating from 10.04 to 10.10, the PC got accidentaly rebooted.
After that I am unable to start even 10.04. A small window tells that GNOME manager didnot install properly.
The PC hangs after tat.
How do I restore the 10.04 version without reinstalling it.

Urgent solution reqd.

---

### Post by dino99 on 2010-12-27
boot from outside (livecd or other linux) then chroot to this broken one following this example:

[http://ubuntuforums.org/showpost.php?p=7929196&postcount=11](http://ubuntuforums.org/showpost.php?p=7929196&postcount=11)

when done, you can continue the previous upgrading. If that fail, clean the cache: sudo rm /var/cache/apt/archives/* , then update again & upgrade.

---

### Post by raunhar on 2010-12-28
The correct error is GNOM power manager not configured.

---

### Post by garvinrick4 on 2010-12-28
After the chroot command in post 2's link.
```
dpkg --configure -a
```
Should configure for you.

---

### Post by raunhar on 2010-12-28
I tried to follow the above steps , but without success. On the GRUB menu ( GRUB 1 version) I tried both : normal and recovery mode, but could not get  to that point

---

### Post by garvinrick4 on 2010-12-28
You have to use a live cd or another install of linux to run commands.
You have to know your sda# of install. Like sda1 or sda5 whatever yours is.
```
sudo fdisk -l
``` (lower case L)will find your linux install.
Give me your install sda number and I will give you code real quick.

---

### Post by raunhar on 2010-12-28
It is sda6 .
I have Ubuntu 9.04 Installation CD.

Pl. provide a step by step solution, as I am not tha good at LINUX operations.

---

### Post by garvinrick4 on 2010-12-28
In a live cd (Ubuntu install cd using Try Ubuntu) with internet connection working. Open a terminal and copy and paste these:
                    ```
sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
exit
```                         ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo reboot
```Hopefully it finished configuring install

---

### Post by jason mathisen on 2010-12-28
hi i have a similar problem     my dell mini was interupted during an update and now i get an error message the reads    dpkg configure a          ive tried to open a terminal but this problem has really messed up my computer.....i can no longer open up my accessories to access the terminal  plus i seem to have lost all my internet wireless connection because i can no longer access my wireless network.......sorry but i know very little about this ubuntu so you may have to walk me through this one step at a time    any help would be great
thanks jason

---

### Post by dino99 on 2010-12-28
@jason

boot on recovery mode (hold "shift" key down at end of bios process if you dont see grub menu by default)

then you can continue with the command line. Look below for more info.

---

### Post by jason mathisen on 2010-12-28
hi i held down the 2 button when it was restarting....this blue screen with all these options popped up......is this what you are talking about.....where do i go from here.....i really need specific directions 
thanks
jason

---

### Post by jason mathisen on 2010-12-28
hi i held down the 2 button when it was restarting....this blue screen with all these options popped up......is this what you are talking about.....where do i go from here.....i really need specific directions......im used to my imac and not this dell inspiron 
thanks
jason

---

### Post by jason mathisen on 2010-12-28
ok now i fixed the configure a part
 now it says i have 18 broken packages


how do i fix them
any help would be great
thanks
jason

---

