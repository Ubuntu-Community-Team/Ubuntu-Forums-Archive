---
title: "Installing Win  XP for dual boot after installing ubuntu"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by des4ij on 2006-10-26
Hey, just wondering, is there a way I can install Win XP after I have installed Ubuntu... i.e. will my computer not screw up if i reszie ubuntu partition, install XP, install grub(not ubuntu) again... or wud i just have to install ubuntu all over again???... 

Also, I wanted to network with my desktop(win XP)... googled it and conclusively installed samba... now i do see my ubuntu computer in MSHOME but it is unaccessible, i.e. it does ask me for password but it wont take in any password... basically it will keep on asking me for a password, i have tried  my laptop password, root password, 1111, 1234, 7890, 0000, and some random stuff... no luck... any idead???...

---

### Post by des4ij on 2006-10-26
Edgy is out... beta was gr8... :)... gonna get that... maybe i'll install windows then edgy **if** i cant install windows after ubuntu :)... but i really dont want to format... any ideas appreciated...

---

### Post by nkassi on 2006-10-26
That should be possible with gparted and a live cd (I know that it is possible without resizing because I have done it many times)

Use a livecd such as the gentoo minimal live cd (gentoo.org) and once booted up:

mount /dev/hda* /mnt/gentoo (* is the drive number of ubuntu and on the gentoo live cd /mnt/gentoo is already created)
mount -t proc none /mnt/gentoo/proc
mount -o bind /dev /mnt/gentoo/bind
*** if you have a seperate boot partition mount it to /mnt/gentoo/boot ***
chroot /mnt/gentoo /bin/bash
grub
(once in grub)
root (hd0,0) (assuming your boot or ubuntu partition is on /dev/hda1. the naming is as follow hda = hd0, and the partion number is the linux number -1 so hda1 = hd0,0 in grub speak)

setup (hd0) 

quit

exit
reboot

done


Nic

---

### Post by nkassi on 2006-10-26
If that sounds way too complex just tell me. I try to make it clearer.

Nic

---

### Post by des4ij on 2006-10-27
Hmm... took me a while to figure out what you were talking about... its a bit clear now... but the thing is I want to install XP on a completely diff partition that i would create using free space on my hard drive after I resize my ubuntu partition... I just dont know if both both OSes will boot through grub then...

---

### Post by Archmage on 2006-10-27
> **des4ij said:**
> Hmm... took me a while to figure out what you were talking about... its a bit clear now... but the thing is I want to install XP on a completely diff partition that i would create using free space on my hard drive after I resize my ubuntu partition... I just dont know if both both OSes will boot through grub then...

After installing Windows you would need to reinstall GRUB. Than you could enter the Windows-Partition as an additional partition to boot from.

---

### Post by Jan Hrbacek on 2006-12-01
Using the Desktop/LiveCD and Overwriting the Windows bootloader
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).
3. Type "sudo grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot. 

I have done this and now I can boot Ubuntu again. 

Few questions:
1) With the procedure above: is grub located in /boot or in MBR?
2) If it is is MBR, how do I access its configuration file?
3) Is it safe to erase all files in /boot/grub?
4) What shall the script in menu.lst look like to enable WinXP booting via grub?

Thanks.

---

### Post by bulldog on 2006-12-01
If you did setup (hd0) it's in your MBR.
You can configure GRUB by menu.lst ```
gksudo gedit /boot/grub/menu.lst
```

I should definitely not erase all the file in /boot/grub.](*,) 

To add XP ad your menu.lst it should look like something like this,
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

---

### Post by Jan Hrbacek on 2006-12-01
Yes, thanks for help Bulldock, you are right.

---

