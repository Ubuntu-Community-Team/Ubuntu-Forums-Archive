---
title: "Problems upgrading"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by AndreSantos on 2008-02-20
I just upgraded kubuntu(7.04->7.10). But now, after the loading screen, there is just a black screen. Its not showing the login screen, what can i do?

Im on an Amazon PC, kubuntu 7.04 was installed on it by default.

---

### Post by PmDematagoda on 2008-02-20
What are the specifications of your PC.

---

### Post by AndreSantos on 2008-02-20
Its a Amazon Pc a601 notebook.

Turion X2 64 TL50 1.6GHz
2 GB SODIMM DDR-2 533/667 GHZ

---

### Post by PmDematagoda on 2008-02-20
What is the VGA card that it uses?

---

### Post by AndreSantos on 2008-02-20
Im not sure, i think its a GeForce.... i think Go 6100

---

### Post by PmDematagoda on 2008-02-20
> **AndreSantos said:**
> Im not sure, i think its a GeForce.... i think Go 6100

Ok, boot Ubuntu in Recovery Mode and then execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then reboot the PC using:-
```
reboot
```

See if that solves your problem at least partly.

---

### Post by AndreSantos on 2008-02-20
Sorry, but how can i boot kubuntu in recovery mode? Im new to all this linux stuff, thanks.

--Found it in Grub menu. Im rebooting atm.

edit: It worked, thanks for the help man.

---

### Post by AndreSantos on 2008-02-20
Maybe i can get a little more help here?
My internet wireless isnt working anymore and my cdrom drive isnt too...

---

### Post by PmDematagoda on 2008-02-20
I cannot help much with the wireless connection, but what problems are you facing with the CD-ROM?

---

### Post by AndreSantos on 2008-02-20
The cd is recognized, then i click to open in a new window.
When it opens, i cant access the cdrom content, and at the botom of the screen i can read:

"The file or folder /media/$A%$|Ä%$* does not exist."


$A%$|Ä%$ -> strange simbols...

---

### Post by PmDematagoda on 2008-02-20
Post the outputs of:-
```
cat /etc/fstab
```
and
```
cat /etc/mtab
```

---

### Post by AndreSantos on 2008-02-20
mtab

```

/dev/sda1 / reiserfs rw,notail 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda3 /media/sda3 reiserfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0

```

fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d4d7afd-e030-4e13-8b8b-91be9246afd0 /               reiserfs notail          0       1
# /dev/sda3
UUID=ba9c492f-64e5-4e69-a045-9425b0302704 /media/sda3     reiserfs defaults        0       2
# /dev/sda2
UUID=de76964d-1ce9-49a3-9b72-37cd605e421a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

