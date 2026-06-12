---
title: "Complete noob - Installation of Ubuntu 7.10 using 2 hard disks"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by craigymcfly on 2008-02-04
Hi all.
Not sure if this is already in the forums because i'm not sure what to search for specifically.

I have :
an old P3 333mhz 
256mb ram
1 x 200gb IDE hard disk (master)
1 x 120gb IDE hard disk (slave)

I want to install ubuntu 7.10 server edition as a server to store photos, videos and music.

I am having trouble with treating the 200 and 120gb drives as one large 320gb drive. After looking through the installation process, i am given options to install with lvm - should this be the way to go?

Ideally, I would like the follwing structure so that i can map the drives via samba to view on my xbox / windows PC and  UPNP on the server to view files on my PS3.

/home/tv
/home/music
/home/movies
/home/pictures

Do i need to allocate space to each folder above?

I would prefer to install LAMP as i can play around with the web server side too.

My main hurdle to overcome is the allocating / merging of the 2 hard disks into 1.

Does any one have any tips / tutorials into how to achieve this?
Many thanks for any help. 

Craig

---

### Post by jago25_98 on 2008-02-04
You can set it up in all sorts of ways.

Probably the simplest is to have your operating systems on one drive and your data on the other.

In linux this would be:

drive 1, one big partition: / (root)
drive 2, one big partition /home

This keeps it nice and simple. It's a standard thing and it's a good idea. Yes you could do some interesting stuff with LVM to give you more storage data and less OS space but I recommend keeping it simple to begin with. 


If you're dual booting with Windows you might want to consider splitting both drives in the same way with a 2nd partition on each drive.

These are the simplest ways of doing it. You can get more complicated stuff like ext2 linux filesystem drivers for windows but I recommend keeping it simple, it saves hassle down the line.

---

### Post by craigymcfly on 2008-02-04
thanks for the reply.

I am not intending it to be a dual boot system. Just purely a ubuntu server.

---

### Post by craigymcfly on 2008-02-04
> **jago25_98 said:**
> You can set it up in all sorts of ways.

Probably the simplest is to have your operating systems on one drive and your data on the other.

In linux this would be:

drive 1, one big partition: / (root)
drive 2, one big partition /home

This keeps it nice and simple. It's a standard thing and it's a good idea. Yes you could do some interesting stuff with LVM to give you more storage data and less OS space but I recommend keeping it simple to begin with. 


If you're dual booting with Windows you might want to consider splitting both drives in the same way with a 2nd partition on each drive.

These are the simplest ways of doing it. You can get more complicated stuff like ext2 linux filesystem drivers for windows but I recommend keeping it simple, it saves hassle down the line.

would drive 1 as one big partition mean less space on the /home partition? Ideally i want a small partition for installation and the remainder as storage

---

### Post by forestpixie on 2008-02-04
drive 1 and 2 would be separate - another way to do it would be to have /, /home and swap on one drive and have the second as purely data storage - it's how I do it

not sure how to treat the 2 drives as 1 - nor whether having seperate /home/pictures, movies etc would be a good idea - if they are all just folders within /home you won't have to worry about making sure there's enough room in each

depending on how much you're installing have / at 10 or so Gb, however much swap as you feel you need and the remainder could be /home - the other drive would be /media/something

---

### Post by craigymcfly on 2008-02-04
thanks

i think i've got somewhere to start from.

When i install the server from the cd, which options should i use in terms of the drives?

---

### Post by forestpixie on 2008-02-04
As I've never actually installed the server version which I believe to be a text based install I would make sure I had the partitioning sorted out beforehand - which I tend to prefer and recommend anyway :)

I use gparted livecd - download, burn as an iso and boot with it - but (assuming the drives get assigned as sda) I'd go for sda1 15Gb, sda2 - whatever is left, make an extended partition and create inside a swap partition - if you're going to be putting more ram allow for that - but you can later make swap fairly simply

the other 120Gb drive will just be one partition - sdb1

so that would be 

sda1 15Gb - when you get to the partition part of the install it's mount point needs to be /
sda2 184Gb - that'll need mounting as /home
sda5 1Gb - mount as swap or format as swap can't remember

sdb1 - should get picked up by the install and given a mount point, if it doesn't go for something along the lines of /media/data - or your own jazzy name 

when you're in gparted you can format the partitions as you go

that would give you 204Gb to use as data storage, once you're done you can then make you're media directories inside /home as you wish

Final point - just want to make sure that you know that once you've installed the server edition you will not have a desktop and will need to do everything with the cli - title says noob so just clarifying :D

---

### Post by craigymcfly on 2008-02-04
thats really helpful. Thankyou.

I will need to try it when i get home though.

---

### Post by craigymcfly on 2008-02-04
ok, i burnt the cd and partitioned the drive

however, ubuntu did not recognise it and partiotioned it itself.

After the lengthy install, there was a problem with the grub loader

going to try again tomorrow

:confused:

---

