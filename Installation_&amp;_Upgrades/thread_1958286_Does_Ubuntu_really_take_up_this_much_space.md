---
title: "Does Ubuntu really take up this much space?"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by rickyhart91 on 2012-04-14
I'm trying to install Ubuntu on my Acer (currently runs Windows 7). I clicked the option to wipe off Windows 7 and replace it with Ubuntu 11.10. The next screen showed that it would take up 160GB, my whole drive space. Is this just the OS, or did it allocate room for programs, pictures, etc. in that number too?

---

### Post by Lemuriano on 2012-04-14
Hi, 

The OS would take less than 10g and the rest is available.
I would suggest to make a partition for the OS like 12 to15 g, one for swap and the rest for your home folder. That would help in case you need to reinstall because your files and setting would be there.  
 
Regards.

---

### Post by cbennett926 on 2012-04-14
> **rickyhart91 said:**
> I'm trying to install Ubuntu on my Acer (currently runs Windows 7). I clicked the option to wipe off Windows 7 and replace it with Ubuntu 11.10. The next screen showed that it would take up 160GB, my whole drive space. Is this just the OS, or did it allocate room for programs, pictures, etc. in that number too?


What it's doing is reformatting it and "giving" your harddrive to Ubuntu. However, as someone else mention you could pop in a Live CD and partition it with G-Parted and cut that down to about 25 gigs (I like round numbers :) )  and then use the rest for whatever, unless you want a full Ubuntu install which is great too!

EDIT:

Also, when you install, you can go to "Advanced Options" on the screen where it asks if you want to use the whole drive, and you can partition it from there!

---

### Post by oboedad55 on 2012-04-14
> **rickyhart91 said:**
> I'm trying to install Ubuntu on my Acer (currently runs Windows 7). I clicked the option to wipe off Windows 7 and replace it with Ubuntu 11.10. The next screen showed that it would take up 160GB, my whole drive space. Is this just the OS, or did it allocate room for programs, pictures, etc. in that number too?

If during the install you chose to let Ubuntu make the choices for you then it would use the whole hard drive. The actual install itself needs far less space than that. If you want, you can boot with the LiveCD and set up the partitions you want in advance using Gparted.. You can look at the Wiki here;

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

It will give some suggestions and ideas for partitioning. I like to have at least a root partition / and a separate /home partition in addition to a /swap partition. With a separate /home partition if you need to reinstall or what have you you can keep all your data and settings. You'll find all sorts of ideas for the /swap size, but what I've always done is make the size of /swap the same as my RAM, i.e. I have 4 gigs of RAM so I make a 4 gig swap partition. If you want to hibernate you'll need at least that much space.
I hope that gives you some ideas. If you need more help just post back.

---

### Post by rickyhart91 on 2012-04-14
This is my first time installing an OS to my computer so I don't really know all the technical jargon, could you guys simplify it for me?

---

### Post by Curtis6767 on 2012-04-14
Have you read this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Answers lots of questions about installs.

---

### Post by newbie-user on 2012-04-14
Partitioning means to divide up the hard drive space. You could cut up your 160GB into, say, four 40GB partitions. When the Ubuntu installation says it's going to use 160GB, it just means that the whole hard drive will be in one partition.

Are you using a LiveCD to install Ubuntu or an alternate CD?

---

### Post by rickyhart91 on 2012-04-14
> **newbie-user said:**
> Partitioning means to divide up the hard drive space. You could cut up your 160GB into, say, four 40GB partitions. When the Ubuntu installation says it's going to use 160GB, it just means that the whole hard drive will be in one partition.

Are you using a LiveCD to install Ubuntu or an alternate CD?

I'm using a flashdrive.

---

### Post by dino99 on 2012-04-14
here is how to set the partitions:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

then when installing via the "alternate" iso, choose the "manual" installation

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by rickyhart91 on 2012-04-14
So would this be correct?

/dev/sda
  >/dev/sda1 ext4 /:root   12287 MB
  >/dev/sda5 swap           4094 MB
  >/dev/sda6 ext4 /home  143655 MB

---

### Post by Lemuriano on 2012-04-14
Hi,
 
Just boot from the usb drive and answer a few questions, it´s very intuitive.
 
Regarding the HDD you have several option:
 
1- Install Ubuntu in one partition, the easiest one. On installation types the option would be very clear about choosing  only Ubuntu for the whole disk.

2- Make several partitions, the best option. For this you chose ¨Something else¨ and I encourage you to read the links posted in this tread about installation. 

Hope this helps,
Regards.

---

### Post by rickyhart91 on 2012-04-14
> **Lemuriano said:**
> [FONT=Ubuntu Condensed]Hi,
 
Just boot from the usb drive and answer a few questions, it´s very intuitive.
 
Regarding the HDD you have several option:
 
1- Install Ubuntu in one partition, the easiest one. On installation types the option would be very clear about choosing  only Ubuntu for the whole disk.
[/FONT]
[FONT=Ubuntu Condensed]2- Make several partitions, the best option. For this you chose ¨Something else¨ and I encourage you to read the links posted in this tread about installation. [/FONT]

[FONT=Ubuntu Condensed]Hope this helps,[/FONT]
[FONT=Ubuntu Condensed]Regards.
[/FONT]

But would the 160GB it says that it would take up be just the OS or does that include space for files I might download?

---

### Post by Lemuriano on 2012-04-14
That look nice as long as you have 4g of ram.;)

---

### Post by rickyhart91 on 2012-04-14
> **Lemuriano said:**
> That look nice as long as you have 4g of ram.;)

How would I allocate space for ram?

---

### Post by Lemuriano on 2012-04-14
> **rickyhart91 said:**
> But would the 160GB it says that it would take up be just the OS or does that include space for files I might download?

The 160g would be available for the OS and all the files you download. It´s just one partition for everything.

Regards.

---

### Post by rickyhart91 on 2012-04-14
> **Lemuriano said:**
> The 160g would be available for the OS and all the files you download. 

Regards.

Ok, thanks. I didn't expect it to take this long for my original question to get answered though:shock:

---

### Post by Lemuriano on 2012-04-14
> **rickyhart91 said:**
> How would I allocate space for ram?

The swap partition should be at least equal to the amount of ram that you have, specially if you use hibernation. You don´t need a ram partition.

Regards.

---

### Post by Lemuriano on 2012-04-14
> **rickyhart91 said:**
> Ok, thanks. I didn't expect it to take this long for my original question to get answered though:shock:

On my first post I try to address your question. When I said ¨The OS would take less than 10g and the rest is available.

Regards.

---

### Post by QIII on 2012-04-14
The reason the answer took so long is that there is a trivial install method (just let it do the default setup) and a slightly more involved method most of us prefer for the simple fact that it creates a "separate /home partition", which is a very desirable layout for several reasons - which is beyond the scope of just a post or two.  And since we all have our own opinions about the details, you get lots of suggestions.

(Do you know how many geeks must be in a room before you have a disagreement?  One.)

Someone posted a link to some installation info, which you should read.

Don't bother with a /boot partition.  It is generally unecessary in a Linux system unless you have a particular specific need.

My recommendation:

Create

One ext4 partition of 12 - 25 GiB mounted at /
One swap partition equal to 1 or 1.1x memory
One ext4 partition taking up the rest of the disk at /home

---

### Post by rickyhart91 on 2012-04-14
Thanks for your help guys, I got it installed and I already love it more than Windows 7.

---

