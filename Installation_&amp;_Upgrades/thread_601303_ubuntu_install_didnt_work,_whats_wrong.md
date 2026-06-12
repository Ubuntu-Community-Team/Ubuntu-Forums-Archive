---
title: "ubuntu install didnt work, whats wrong?"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by trixorz on 2007-11-03
i have just installed ubuntu on my home computer, but after the installation i cannot get it to boot. if i press alt+f1 i just get the loading, please wait... screen and then after some time a error messege pops up and i it runs somthing called busybox instead

the error  messege is:
"check root= bootarg cat /proc/cmdline
or missing modules, device: cat /proc/modules 1s /dev
ALERT! /dev/disk/by-uuid/d81db337-403e-4dce-b1df-bd8bf7a67669 does not exist. Dr opping to a shell"

i can't find any place with answers to why it does it and i have no idea whats wrong

---

### Post by American_Outcast on 2007-11-03
Try reinstalling grub with the livecd/install disk.

Here is a link that explains it more.

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)


EDIT: It shows you a few different ways to reinstall grub. I usually do it this way,

> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.


EDIT again: I just noticed something. Where did you install Ubuntu? IDE, SATA, USB?

---

### Post by trixorz on 2007-11-03
hmm, ive tried some time now to figure out how to do what you posted American_Outcast
but i have some problems with doing it.
my harddisk and boot partetion numbers are, and as far as i was able to see the forum post you linked to didnt show it (might have missed it?)
and that other method posted in the link didnt work for meeither as if i do like it says in manuel it does not come with any errors and it will format my disks and i do not see any option to jump to the "install grub" thing

would you care to help me a bit more?

---

### Post by American_Outcast on 2007-11-03
>  ALERT! /dev/disk/by-uuid/d81db337-403e-4dce-b1df-bd8bf7a67669 does not exist. Dr opping to a shell"


It looks like it is saying where you installed Ubuntu, the drive isn't there. Do you know where you installed it?

---

### Post by trixorz on 2007-11-03
well, when i installed it i formatted the disk, and i make a 2000 mb disk for ubuntu (the swap) and the rest on another partition.
but i do not know how to find the names on the partitions :S

if it helps in root terminal where i first did "cd /mnt/ubuntu"  do no ask me what that line does, it was somthin i found in that other post.
but if i in that folder do fdisk -l   i get 3 devices
/dev/hdc1     which has a * at boot id is 83 and it says linux is the system
/dev/hdc2     no star at boot     id is 5     system: extended
/dev/hdc5     no star at boot either    id is 82  system: linux swap / solaris

---

### Post by American_Outcast on 2007-11-03
What does > sudo fdisk -l say?

---

### Post by trixorz on 2007-11-03
device:          boot:       start       end       blocks            id        system
/dev/hdc1      *             1            27959    239039136     83       Linux
/dev/hdc2      n/a            29760     30515   6072570         5         Extended
/dev/hdc5      n/a            29760     30515   6072538+       82       Linux swap / solaris

---

### Post by American_Outcast on 2007-11-03
> **trixorz said:**
> device:          boot:       start       end       blocks            id        system
/dev/hdc1      *             1            27959    239039136     83       Linux
/dev/hdc2      n/a            29760     30515   6072570         5         Extended
/dev/hdc5      n/a            29760     30515   6072538+       82       Linux swap / solaris


With the live cd/install disk can you access the hard drive files? If so can you get to the /etc/fstab file on the hard drive, not the cd, and cut and paste it here?


There is another way you can do this to. I believe nano is on the livecd/install disk.

In the terminal type 

sudo nano /etc/fstab 

and paste what it says here

then type 

sudo nano /boot/grub/menu.lst

and paste what it says here

---

### Post by trixorz on 2007-11-03
when i go to places --> computer --> filesystem i can check my hdd fileson it (it i the 2000 mb partition)
anyways from that path i go to etc-->fstab
and it says:
"unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0"

---

### Post by American_Outcast on 2007-11-03
I always have a had time explaining things. I am great at hands on but thats about it, lol.

Are you duel booting? If not maybe you could try to reinstall Ubuntu. If you have any memory cards, usb drives, etc, make sure they are not hooked up if you reinstall.

Your hard drive is there but it looks like grub is pointing somewhere else looking for everything.

Is there someone here who is better explaining things then I am? If so please jump in so I don't confuse trixorz, lol.

---

### Post by trixorz on 2007-11-03
well, i did have windows vista before (which i didnt like)
could that be why?
as im not sure if it formats everything on the drive when i install ubuntu

btw i have tried reinstaling 4 times now, so im not to confident that it would work :S


anyways it is installing now, i selected the option to delete all partetioning on it and hope that would work (yes i have backup :P )

---

### Post by American_Outcast on 2007-11-03
> anyways it is installing now, i selected the option to delete all partetioning on it and hope that would work (yes i have backup :P )

If it still doesn't install and boot then I am lost. Maybe it is a bug of some sort or the hard drive is on its way out?

---

### Post by trixorz on 2007-11-03
damn, it still doesnt work :S
is there anyway that in that busybox menu i can get it to boot?
do you think it would help if i formatted the drive?

(anyways thanks for the help so far, it was nice :D )

---

### Post by American_Outcast on 2007-11-03
Sorry I was away for a bit. I was hoping your problem would have been resolved.

Do you have only one hard drive? If so it is saying it is hdc. If you only have one hard drive play around with the cables or jumper settings on your Hard Drive, (For example if it is set to slave change it to cable select or main.) Also see what your bios says. Make sure that it is booting the hard drive first (or second after the cd drive.)

I think what is happening is that Ubuntu is reading what your bios says and your bios is saying the hard drive is /dev/hdc when it is not. Also if this is your only hard drive it may be trying to write the MBR to /dev/hda but /dev/hda/ doesn't exist.


Edit: Also is the hard drive an IDE, Sata, Pata, etc?

---

### Post by trixorz on 2007-11-04
it is a ide harddrive and i only have one
im at work atm so i cant check bios yet, but i will try and do that when i get home and then find out if it works

---

### Post by trixorz on 2007-11-04
hmm, i cant find anything in the bios, the drive is starting up as number 2.
i checked the disk and it was set to master, does it matter which of the 2 IDE ports i use on the mainboard? as it has 2 different IDE ports.
and i tried to put it on cable select which didn't work either.

---

### Post by alina.bolero on 2007-11-05
I've been going thru the same headache.  [http://ubuntuforums.org/showthread.php?p=3690885#post3690885]("http://ubuntuforums.org/showthread.php?p=3690885#post3690885")

There seems to be a kernel option that got FUBARed after a recent Gutsy update.  My system used to work perfectly fine!!!!!!

I've been fighting this one for a few days now.

---

