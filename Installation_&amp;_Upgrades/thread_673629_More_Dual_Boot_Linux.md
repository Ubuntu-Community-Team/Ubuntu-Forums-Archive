---
title: "More Dual Boot Linux ????"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by pepperwood on 2008-01-20
Have been working on the trying to install Fresh Dual Installation w/2HDD's for Ubuntu EMC2 & Linux BDI EMC and the being able to choose the OS on BOOT. 

This Senior CZ & Newbie has been at this ALL year so what would you expect?? My HDD's are set Master/Primary & Slave/Secondary. Must have tried just about every type/way of installing, that is except the right way. Cannot get startup screen to show both OS.

Have use Automatic partition & have looked into Manual. The installation CD's work . But somewhere I'm making the wrong choices when trying to set up a Druid. I've setup Ubuntu to install on /dev/hba1 from the start. Plan on setting up BDI at /dev/hba2. What do you all think?

So I have a couple of questions to ask?? When it comes to the partitions what do I designate the partitions & how much space allowed for each as my Druid doesn't cover this as well? Thank you for your patience, understanding & taking the time to help.

Kindest Regards,
Pete

---

### Post by torgrot on 2008-01-20
I don't know much about those versions, but what I looked at you should be able to install the Linux BDI EMC version first to one hard drive and then the Ubuntu EMC2 to the other hard drive.  Ubuntu;s grub installation program is pretty good at picking up additional operating systems, so it should have entries for both when it is done.  Do you have Windows installed on the hda drive?  As far as partition sizes, I don't know how much space each of those programs take up so I couldn't even hazard a guess as to size.

torgrot

---

### Post by pepperwood on 2008-01-20
I don't know much about those versions, but what I looked at you should be able to install the Linux BDI EMC version first to one hard drive and then the Ubuntu EMC2 to the other hard drive. Ubuntu;s grub installation program is pretty good at picking up additional operating systems, so it should have entries for both when it is done. Do you have Windows installed on the hda drive? As far as partition sizes, I don't know how much space each of those programs take up so I couldn't even hazard a guess as to size.

Hi Torgot - Got your note! Thanks for the reply. I've been installing both vise versa & versa vise. Lost count of the times. Using Auto Formatting. Each CD installs its OS perfectly on their HDD's. They just both don't show up on the start-up screen.

Hoping to use Druid or Manual and hopefully get set this year. It'll be a learning process.  Thanks again!

Pete

---

### Post by torgrot on 2008-01-21
After you have them both installed you could take a look at this page [http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot](http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot).

So after you have installed both and have ubuntu working you could follow the steps there to boot the second operating system directly.

torgrot

---

