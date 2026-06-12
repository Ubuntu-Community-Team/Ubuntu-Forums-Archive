---
title: "Ssd"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by ubunterooster on 2010-04-27
My First SSD arrives soon. Are there any differences to a HDD in how to format/install/whatever?

---

### Post by Herman on 2010-04-27
:) You can just install Ubuntu in an SSD in exactly the same manner as you install in a HDD, and it will perform extremely well.

If you want to milk every last drop of possible speed out of your SSD, there are a lot of things you might be able to do, but those are specific to the exact make and model of SSD you have. You should explore the web forum provided by your SSD's manufacturer and search for the best advice there, for your exact make and model, since they're all different.

What kind of SSD drive are you getting anyway? (If I may ask?)  :)

---

### Post by ubunterooster on 2010-04-27
A 128 gb patriot torqx. MaximumPCs "best-of-the-best." It comes Saturday, I think, so I have time to prepare.

---

### Post by Herman on 2010-04-28
:) Nice! One of those should run Lucid Lynx so fast it'll make you do back flips! Make sure you fasten the seatbelt on your computer chair! :)

I found the [Patriot Forums SSD Support]("http://www.patriotmem.com/products/groupdetailp.jsp?prodgroupid=114&prodline=8&group=Torqx%20Solid%20State%20Drives&catid=21") section for you, just in case you haven't already found it. It looks like there are already a few other Ubuntu users there. 

You may want to align your partition up on erase block boundaries before  you begin your installation. Check with Patriot Forums to find out what  the erase block boundaries are for your SSD.

Probably the most important settings for any kind of flash memory (in my opinion), would be setting up GRUB2 to boot your Linux kernel with either the noop or the deadline IO scheduler.

Download the latest version of hdparm so you can get wiper.sh out of it, and install DiskTrim for keeping track of your disk writes and running wiper.sh for you.

Experiment with settings for swappiness and see which setting suits you. A lot of people advise setting swappiness to 0, but I  found that slowed my system down, and my system seems to work best with a swappiness value of 10.

It's also possible to tune the ext4 file system up so it's aligned with erase block boundaries. Once again your Patriot Support Forum would be the best place to go looking for specific advice on that subject. Probably a standard setting for all flash memory would be to set 'noatime' as a mount option in /etc/fstab.

If you need me to elaborate then just ask me and I'll go into more details.

It's worth repeating though, that while most of those things do help a little and make the uber fast even a wee bit faster, and are kind of fun to play around with for those of us who love the command line and are keen to learn more about our computers, they are not really necessary. Almost anyone can just install Ubuntu in a SSD drive and have very snappy performance without doing anything special at all. The extra tweaks are just for fun really.

Woo-Hoo! You'll be getting your new SSD shortly after Lucid will be released! Good timing! \\:D/

---

### Post by ubunterooster on 2010-04-28
I think I'll be forgoing any unneeded steps for this time but may reinstall and tinker later. Right now I feel pretty jaunty. :D So thanks again, Herman. 
[btw: your first post would not have reached me last night had it been posted but 20 seconds later. Cool, no?]

---

