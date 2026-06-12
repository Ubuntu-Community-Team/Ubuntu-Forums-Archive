---
title: "Nothing effect repair &quot;no init found&quot; with use fsck -y /dev/sda1"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by n3wguys on 2015-01-22
Hi, I have problem. my ubuntu was crash and only show 

.....
No init found. Try passing init = bootarg


I have tried some solution such as 

1. booting with ubuntu 14.04 live CD
2. sudo fdisk -l
3. sudo fsck -y /dev/sda1

reboot.

nothing solve about this and still show ](*,)

(initramfs)


I have 4 partition directory for my system. and my detail partition on ubuntu 14.04 is

/boot 
/swap
/
/home

thank you so much that your support

---

### Post by silverslide on 2015-01-22
I think I'm having the exact same problem. I can't chroot into the ubuntu installation either. Restorting grub gives errors too. Tried any of these?

---

### Post by n3wguys on 2015-01-22
How to do "Restoring grub" ? I mean the command to do for restoring grub.

---

### Post by Bashing-om on 2015-01-22
n3wguys; Hello;

Reinstall grub, with a separate /boot partition:
From the liveDVD:
```

sudo fdisk -lu ## so you know the partition identifiers
sudo mount /dev/sdXY /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sdX
sudo umount /mnt/boot

```
where 'X" is the drive (say sda) and 'Y' is the partition number ( say 1, as in sda1)

Reboot into the install .. and run:
```

sudo update-grub

```

Any doubts, post the output of ' fdisk' ; and we will advise.

[INDENT][INDENT]hope this works[/INDENT][/INDENT]

---

### Post by n3wguys on 2015-01-25
Hello Bashing-om

unfortunate, I tried again 
connecting direct with internet from Live CD Ubuntu, and try to update && upgrade,perhaps everything could be solve it self. 
but, can't install it(permission denied)

after it, I run again this comment

fsck -y /dev/sda1 
fsck -y /dev/sda7
fsck -y /dev/sda8

and I reboot and boooom... my ubuntu 14.04 is kernel panic.

So tomorrow I will re install again this system.

---

### Post by Bashing-om on 2015-01-25
n3wguys; Welll .....

(RE-)install is a sure way to get resolution; If you do decide to continue to try and fix this install, provide:
```

sudo fdisk -lu
sudo parted -l

```
Then we know how to properly install grub and/or run a file system check .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by n3wguys on 2015-01-25
Bashing-Om,

before kernel panic, I had tried your instruction and run from Live CD. when I mount this device on /mnt/boot /dev/sda1 (maybe)

show warning, not found directory /mnt/boot. after it I create directory on /mnt/

so command is : sudo mkdir /mnt/boot

after that,

I go to command : sudo grub-install --boot-directory=/mnt/boot /dev/sda1

but error : file system 'ext2' does not support embedding, embedding is not possible. Grub can only be installed in this setup by using blocklists. however, blocklists are Unreiable and their use is discouraged.

---

### Post by Bashing-om on 2015-01-25
n3wguys; hummm ..

Should not .. but will not hurt to mount it explicitly:
```

sudo fdisk -lu
sudo mkdir /mnt/boot
sudo mount /dev/sda1 /mnt/boot

```
check the output of 'fdisk' that sda1 is indeed the partition /boot.
Now if you are running a file system check, the Partition(s) MUST NOT be mounted - so they are not in use and the file system is static at that time.

IF you are installing grub, the partition /boot MUST be mounted .

When all done the partition (files system(s)) that you manually mounted MUST be UN-Mounted - else file system corruption WILL result at some level.
To unmount what was mounted as above:
```

sudo umount /mnt/boot

```

If there are continued difficulties. provide the output of :
```

sudo fdisk -lu
sudo parted -l

```

Make sure that you understand the instructions and the state of the file system before executing any commands.
the terminal command:
```

mount

```
will show the mounted file systems.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by n3wguys on 2015-01-25
Bashing-om

step 1
-------------------------------------------------------------------
sudo fdisk -lu ## so you know the partition identifiers
sudo mount /dev/sdXY /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sdX
-------------------------------------------------------------------

after I write:  sudo grub-install --boot-directory=/mnt/boot /dev/sda1 (I'm sure boot directory is here) and then press enter

the warning show after 5 second and I not yet move to  command "sudo umount /mnt/boot"


ok no problem, I finished re install again with disk part partition: perhaps nothing found problem when lost power.

500 mb for /boot with ext2
1G for swap
10G for / with ext4
25G for /home  with ext4

---

### Post by Bashing-om on 2015-01-25
n3wguys; Good ?

I take it from this:> 
ok no problem, I finished re install again

that you are no up and running. All is now good ?

And yes a loss of power can mess up the file system .. In that event I always run a file system check . ( and I hold my breath until the file system check completes) .

A quick way to run a file system check, boot to TTY1 from grub. Log into the system here on TTY1 and execute terminal commands:
```

sudo touch /forcefsck
sudo shutdown -r now

```
Which will reset the fsck file to next boot, and of course 'shutdown' will reboot the system.

[INDENT][INDENT]I hope it is good news coming from you next
[/INDENT][/INDENT]

---

