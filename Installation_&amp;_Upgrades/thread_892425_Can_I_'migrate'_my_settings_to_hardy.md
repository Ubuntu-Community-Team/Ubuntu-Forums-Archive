---
title: "Can I 'migrate' my settings to hardy?"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2008-08-17
I have been running gutsy for the last few months as I got used to Linux. Recently I made a new partition and did a clean install of Hardy Herron from disc. Having played with it for a couple of weeks, I am happy to move over to it completely. 

My original setup has the /home directories on a separate hard drive and all my system on  the other drive which now has four partitions, as per the screenshot attached.

sda 5 contains Hardy 
sda 2 contains Gutsy
sda 1 is the very rarely used xp

Is it possible to move all my settings and configs for installed programs from gutsy to hardy, then clean up the sda2 partition and make that into more data storage space? 

and how can I get Hardy to point to my /home partition on the other hard drive?

Or do I have to setup the desktop and compiz and reload all my programs on to sda 5

Thanks for any help in advance :guitar:

---

### Post by tropdoug on 2008-08-19
bump

---

### Post by tropdoug on 2008-08-20
BUMP

Surely someone can help?

---

### Post by Too Late on 2008-08-20
Well, most of the personal settings and config files are stored in your home folder. So they are on the different disc, not shown in the picture, right?

So, as I understand correctly, there's nothing important on sda2. However, you should verify that yourself. To mount that partition to hardy, go to terminal and type:
```
sudo mkdir /mnt/somethinghere
sudo mount /dev/sda2 /mnt/somethinghere
```
When you are 100 % sure that there's nothing important on sda2, you can easily delete that partition with gparted. After that you can create a new partition, or grow your existing partitions to fill that empty space.

So, your old config files and settings are stored on the different disk. You can temporarily mount that partition in the same way as described above. Then you can copy some files to your Hardy home folder. (Remember that these files are mostly hidden files, press Ctrl+H in Nautilus to make them visible.) You *can* also permanently mount that partition into your home folder (as it was in Gutsy). However, I'm not sure if that (nor the manual copying of files) is very recommended, since not all your programs are having the same version in Gutsy and Hardy. Eg., if you had Firefox 2 in Gutsy and Firefox 3 in Hardy, I don't know if the settings would work "on the fly" or not. However, some (even most) settings will work fine.

---

### Post by tropdoug on 2008-08-23
Thanks too late 

I am in the process of doing that right now, thanks very much for the help.

---

