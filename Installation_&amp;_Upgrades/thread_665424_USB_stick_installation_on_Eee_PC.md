---
title: "USB stick installation on Eee PC"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by punkle on 2008-01-12
Hey I just got a new Eee PC and I am trying to install Ubuntu.

I am using the step by step guide at [https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

I got as far as 

```
sudo parted /dev/sdX set 1 boot on
```

and I got the following error

```
/home/user> sudo parted /dev/sdc set 1 boot on
sudo: parted: command not found
/home/user>
/home/user>
/home/user> sudo parted /dev/sdc1 set 1 boot on
sudo: parted: command not found
/home/user>
/home/user> su
Password:
eeepc-brianflet:/home/user> parted /dev sdc set
1 boot on
bash: parted: command not found

```

As you can see I tried a few things. Can anyone help me with this??

Greatly appreciated!

---

### Post by PmDematagoda on 2008-01-12
Did you execute:-
```
sudo aptitude install syslinux
```
as given?

---

### Post by punkle on 2008-01-12
yeah I did.

I changed onto an Ubuntu system and managed to get this far

```
punkle@punkle-desktop:~$ sudo parted /dev/sdb1 set 1 boot on
Error: The flag 'boot' is not available for loop disk labels.             
Information: Don't forget to update /etc/fstab, if necessary.             

punkle@punkle-desktop:~$ sudo parted /dev/sdb set 1 boot on
Information: Don't forget to update /etc/fstab, if necessary.  

```
and then got this error

```
punkle@punkle-desktop:~$ sudo e2label /dev/sdb1 ubuntu
e2label: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

```

I am a beginner as you can tell.

b

---

### Post by maikie on 2008-01-12
> punkle@punkle-desktop:~$ sudo e2label /dev/sdb1 ubuntu
e2label: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

You get that because you are trying to label a possible fat FS and not a ext(2,3)FS
Try,

> sudo dosfslabel /dev/sdX1 ubuntu

---

### Post by mjrclark on 2008-04-15
I would like to repeat the question about not being able to mark usb/sdcards as bootable with

```
 sudo parted /dev/sdX set 1 boot on

```

which receives 

```
The flag 'boot' is not available for loop disk labels.  
```

as an error.

---

### Post by Ohioan on 2008-04-15
You may want to also look around at [http://www.eeeuser.com]("http://www.eeeuser.com")  

particularly at [http://wiki.eeeuser.com/]("http://wiki.eeeuser.com/")

a standard Ubuntu install MIGHT cause the SSD to prematurly wear out, there are some changes you can apply that will help Ubuntu be more SSD friendly.\

Just some advice.

---

