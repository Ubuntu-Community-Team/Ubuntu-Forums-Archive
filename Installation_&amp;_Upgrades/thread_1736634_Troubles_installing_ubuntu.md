---
title: "Troubles installing ubuntu"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by GershiBelshi on 2011-04-22
Hello,
I am new to ubuntu and linux as a whole. Yesterday, I was trying to install ubuntu 10.10 alongside with my windows vista (dual-boot). On the ubuntu site, it said that the installation was easy, however, it gave me a lot of trouble. I first of all installed it on a USB as the instructions said on ubuntu.com. Everything went as it should and I was soon running ubuntu from my USB. Then, I decided to put it on my hard disk so I clicked the "download ubuntu 10.10" (or something like this) icon that appears on the desktop. It guided me through the steps. Then I got to the step were I have to choose the partition for the hard disk. I hesitated a little, so I decided to quit the installation and do some research online. Then, when I re-did the installation, there was no option to partition the hard disk. There were now only two options, either to overwrite the whole hard disk (which I'm not gonna do) or to set the partitions manually (which I don't think I'm advanced enough to know how to do this). There was no option to get the suggested partition size.

Anyway, so what I decided to do was to delete ubuntu from my USB and then try to reinstall it. However, once again, the suggested partition size option was not available. Then, I tried to give a shot to manually partitioning the hard disk, however, I was too scared to mess up.

Can anyone tell me how I can get the suggested partition size option back? Please, don't try to tell me how to manually do that, I want the automatic option. I really want to use ubuntu because I'm tired of windows and ubuntu just looks cool. I don't want to have to return to windows because of stupid reasons like this.

BTW, I don't know if it's okay to do it according to the forum rules, but this is the second time I'm posting this (because no one really helped me the first time).

Thank you!

---

### Post by sanguinoso on 2011-04-22
Does Windows Vista still boot?

---

### Post by GershiBelshi on 2011-04-22
@sanguinoso yes

---

### Post by Blasphemist on 2011-04-22
Which version are you trying to install? Please run GParted from the try ubuntu and take a screenshot of what it shows. Then post that back here. We can probably tell the situation without more but it could be we'll ask for information from this, [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'll also add this link to a great walk through the dual boot install and it's options. [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by sanguinoso on 2011-04-22
So this dialog doesn't show any more? > Automatic partition resizing (recommended)
Choose the first option, which should say "Install them side by side, choosing between them each startup".
Specify the size of the new partition by dragging the slider at the bottom of the window.
Click on "Forward".
Continue on to Finishing Ubuntu Installation

---

### Post by GershiBelshi on 2011-04-22
[[IMG]http://img200.imageshack.us/img200/5305/screenshotmy.png[/IMG]]("http://img200.imageshack.us/i/screenshotmy.png/")

This is a screenshot that shows the options I get. As you can see, there's no automatic partitioning option.

It's ubuntu 10.10 (maverick meerkat).

@sanguinoso yeah it doesn't show anymore (it did the first time I tried, but now it doesn't)...

By the way, I'm posting this from firefox for ubuntu (which I'm running from my USB flash drive) :smile:

---

### Post by sikander3786 on 2011-04-22
As far as I know, that automatic partitioning option is not available in 10.10. Manual Partitioning is the way to go even if you don't want to, unluckily, I think you would be forced to...

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

---

### Post by Blasphemist on 2011-04-22
This is likely caused by too many (4) primary partitions already existing on the drive. There is an option to do as you want, have the installation handle the partitioning in 10.10, but it won't come up if there are already 4 primary partitions. Run gparted from the try ubuntu off the live cd/usb and post the screenshot(s) please. It may just be that you got far enough in the install yesterday to have a partition created that is still empty and can be deleted in gparted.

---

### Post by GershiBelshi on 2011-04-22
[[IMG]http://img834.imageshack.us/img834/1537/screenshot1uc.png[/IMG]](http://img834.imageshack.us/i/screenshot1uc.png/)

The "/dev/sda2" partition is just a recovery partitioin (instead of giving me a recovery disk, HP made this partition on the hard disk).

Also, I read somewhere that installing ubuntu alongside with windows would make me lose all of my windows information. Is that  true? Is there a way to install it without making a backup (I'll make a backup anyway, I just don't feel like transferring all of my data again).

Thank you once again!

---

### Post by zealibib slaughter on 2011-04-22
I don't know why it isn't giving you the choice anymore but you may want to try 10.04 LTS and see if you get the choice back with it.

---

### Post by Blasphemist on 2011-04-22
Well, you don't have to many partitions and it does look like the live cd/usb install should give you the automatic option to use some of the free space from the sda1 partition. The only thing I can think of might be that windows may have something at the end of that partition that is keeping ubuntu from being able to shrink it. Try a defrag from windows first. My win 7 install has about this size and it is giving me grief because it say it has something at the end of the partition that is unmovable. Please use win defrag and then see if it can shrink that partition. I'm sorry but I don't have vista to be able to tell you the exact utilities steps. You may even have to defrag more than once but lets hope not as it can take a long time depending on the fragmentation.

---

### Post by GershiBelshi on 2011-04-24
Alright, thanks guys. I think I'm just going to wait for the 27th until Natty Narwhal comes out and hope it doesn't give me any troubles. Thanks anyway, though.

---

### Post by Dutch70 on 2011-04-24
Whether you use 10.10 or 11.04, you still need to shrink your hard drive from within vista or you may have a lot of trouble getting vista back. There are several tutorials on the web, here is a couple.
[[COLOR="RoyalBlue"]http://www.bleepingcomputer.com/tutorials/tutorial133.html[/COLOR]]("http://www.bleepingcomputer.com/tutorials/tutorial133.html")
[[COLOR="RoyalBlue"]http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/[/COLOR]]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

