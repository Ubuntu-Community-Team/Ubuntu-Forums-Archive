---
title: "Can Ubuntu be installed on it's own?"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by Jamie_Edwards on 2011-08-12
I'm building my first PC and I've tried researching whether Ubuntu 11.04 can be installed by itself and have had no luck.

I was initially going to buy Windows 7 and then install 11.04. But if it's possible to install the latter by itself then I won't bother paying £119 for the other OS.

So is it possible to install Ubuntu by itself? and if so then how?

Oh and as you can probably guess the HDD is completely new with no OS on it.

Thanks

---

### Post by aeronutt on 2011-08-12
Actually, installing Ubuntu by itself is the easiest way. So yes. I'd recommend you go here, download .iso, burn onto a CD (or USB), boot to the CD (or USB), and install!

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

(Click on the 'show me how' button next to install it, on that page, and it'll give you pretty clear directions.)

---

### Post by papibe on 2011-08-12
Yes, of course. Here's a [tutorial]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-11.04-natty-narwhal-with-ubuntu-classic").

Good Luck!

---

### Post by grahammechanical on 2011-08-12
I did what you are doing in 2007. So, the answer is yes. I got my first copy of Ubuntu as a give away with a Linux magazine. It will be alive CD. so, it will boot from the CD/DVD drive and it will test out your hardware.

May I make one suggestion? Study up on partitioning. If you tell Ubuntu to install using the entire disk it will create two partitions, one for the OS and one for swap. But if you ever need to reinstall you will lose all your data.

It is best (in my opinion) to choose the Do Something Else option and create three partitions. One of about 20GB which you give a mount point of / 

One of about 2GB which you give a mount point of /swap.

The rest you give a mount point of /home. This is where your data and application settings will be kept. Then you can reinstall into the 20GB partition which can be formatted and so long as you do not mark the /home partition to be formatted you will not loose for data.

Here is a link

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")


Regards.

---

### Post by aeronutt on 2011-08-12
^^^^ excellent recommendation.

---

### Post by sanderd17 on 2011-08-12
> **grahammechanical said:**
> I did what you are doing in 2007. So, the answer is yes. I got my first copy of Ubuntu as a give away with a Linux magazine. It will be alive CD. so, it will boot from the CD/DVD drive and it will test out your hardware.

May I make one suggestion? Study up on partitioning. If you tell Ubuntu to install using the entire disk it will create two partitions, one for the OS and one for swap. But if you ever need to reinstall you will lose all your data.

It is best (in my opinion) to choose the Do Something Else option and create three partitions. One of about 20GB which you give a mount point of / 

One of about 2GB which you give a mount point of /swap.

The rest you give a mount point of /home. This is where your data and application settings will be kept. Then you can reinstall into the 20GB partition which can be formatted and so long as you do not mark the /home partition to be formatted you will not loose for data.

Here is a link

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")


Regards.

Very good indeed, but I always have a backup OS. Because I sometimes do strange things with computers, I sometimes mess up the OS. So I have two partitions of 15 to 20 GB with two OS (a current one and a backup). 

If one OS crashes (mostly because I made it crash), I use the backup OS. And if I have to install a newer version, I install it instead of the backup. And what used to be my current gets degraded to my backup OS.

---

### Post by lazerking9 on 2011-08-12
And don't get rid of your installation CD (or whatever you use) once you get your new computer running. If something goes wrong with your system, you always have a self-contained OS to fall back on, either for repair or reinstallation.

---

### Post by Jamie_Edwards on 2011-08-12
Thank you all very much for the replies!

But alas I now have another problem #-o

which is this post here:

[http://ubuntuforums.org/showthread.php?t=1823736](http://ubuntuforums.org/showthread.php?t=1823736)

Hope you guys can help with that too!

---

