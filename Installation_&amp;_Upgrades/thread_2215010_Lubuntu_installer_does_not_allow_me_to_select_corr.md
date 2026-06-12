---
title: "Lubuntu installer does not allow me to select correct hard drive"
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by Brent_Santin on 2014-04-04
Hi guys,

First time Linux user here - gradually making the transition from Windows XP and dipping my toe into Linux.

I am trying to do a permanent dual boot (Windows XP/Lubuntu) installation of Lubuntu on a P4/3GB. Windows XP already exists on the a 160GB drive (Master on primary IDE channel).
There is also another hard drive in the system, a 500GB drive on the primary IDE channel acting as Slave.  This slave drive is my "dump repository" drive for media files when video editing and doing musical audio recording.  I do not want any OS files there. I want to install Lubuntu to the Master 160GB hard drive, alongside Windows XP - I would be happy to split the drive in two - half for Windows XP and half for Lubuntu.

However - the installer has stumped me pretty early into the install process and not able to proceed.  I'll explain what happened.

When I begin to install Lubuntu, I get this screen (click to enlarge any images in this message):

[[IMG]http://s3.postimg.org/hsupo9xi7/screen_01.jpg[/IMG]]("http://postimg.org/image/hsupo9xi7/")
(this is just a stock screenshot I found on the 'net, but it's pretty much the same as what I'm shown)

So I choose the first option "Install Lubuntu alongside Windows XP..."

But on the next screen it appears that Lubuntu is trying to install itself on my 500GB "media" drive (which I do NOT want).

[[IMG]http://s27.postimg.org/gqzs7zf27/IM000404.jpg[/IMG]]("http://postimg.org/image/gqzs7zf27/")

The drop down bar at the top does not allow me to select any other drive than the one that is showing.

So....I go back one step (to the first screen) and instead choose "Something else".

Now I get this screen, which seems to show all my drives.  But it's very confusing and non intuitive.  I don't know what to do, and furthermore, I am terrified to try anything for fear of wiping my Windows XP drive completely.

[[IMG]http://s1.postimg.org/dn5c9zpwr/screen_03.jpg[/IMG]]("http://postimg.org/image/dn5c9zpwr/")

So, now I am stuck.  Not knowing how to proceed in the installation of Lubuntu. 

I consider myself pretty computer savvy (having used computers since 1980) but I find this a little daunting (which is disappointing because I heard Linux was welcoming).

I'm thinking what I want to do can be accomplished through the software installer, but if not, I could just unplug the 500GB drive from the IDE cable and then try the install on the 160GB drive alone.  However, it seems to me that this is something that should "just work" out of the box...the basic installer should allow me to select the drive of my choice in screenshot two....so what am I doing wrong?

Can anyone provide any advice?  Thanks.

---

### Post by ajgreeny on 2014-04-04
In spite of your earlier comment you could quite easily install Lubuntu  to the data disk thereby not interfering with XP at all, and that would  be my recommendation.  As that disk is not an OS disk there is no way  that it could damage your XP system in any way, and you could definitely  shrink that sdb1 partition at installation time with no fear of  repercussions.

Are the second and third screenshots from your actual attempt to install?

If so, and you really wish to install to your XP disk, you need to shrink partition sda1, but I am uncertain if XP has its own disk management utility which allows you to manage partitions in the same way that Vista and later versions have.  If it does, you should use that rather than any other way to make some free space at the end of the partition of the size you want.  As you have a separate data disk you may not want a very large partition for Ubuntu, about 20 GB would be plenty for the root, (or the operating system), partition, and you can then link folders in your data disk to the standard /home folders of Lubuntu, so the data files are not moved but will appear the ubuntu partition when you look for them in Documents etc folders.

If XP has no disk management system you will need to use a third party partition manager, and I suggest **gparted** from the live Lubuntu system should be fine as long as you leave the start point of XP at the front of the drive and move the right hand end back as far as you need.  Once you have shrunk the partition I suggest you boot back into XP to allow it to run checkdisk and assure yourself that it will still boot before you install Lubuntu.


Having made the space you then use the "Something Else" option and point the Lubuntu installer to the free space in sda1.  Choose to make a **new partition**, make it **ext4** filesystem, use **/ as the mountpoint**, and make sure the **Format** box is selected.

I always recommend using the "Something Else" option when installing as it gives a lot more certainty about what you are doing and what is going to happen.

Once the OS is installed we can help you set up the links to the data disk folders in your Lubuntu  home.

Good luck.  It may all look very complicated at the moment, but once you have done it and succeeded, it will all feel much simpler to you.

---

### Post by Brent_Santin on 2014-04-04
Thanks.  I was instructed on several forums (before installing Lubuntu) that the Lubuntu installer would automatically help me through the re-partitioning of my 160GB hard drive (the drive already containing Windows XP).  I would like to "shrink" the XP partition and install Lubuntu on the same drive, thereby leaving my other drive (the 500GB drive) available for multi-media project files.  

Essentially, I would like Lubuntu installer to manage the creation of a new partition on my Windows XP hard drive, and install Lubuntu there.  But for some reason, on the second screen-shot above I cannot select the 160GB drive from the drop down near the top of the window.  The only drive that is displayed and available is the 500GB drive.  Why, I do not know - and that is my problem.

Yes, the second and third screenshots are from my actual installation attempt.

---

### Post by ajgreeny on 2014-04-04
OK, so when you get to the point shown in the third picture, ie, having chosen "Something Else", can you now select the partition sda1 then click on the Change button, bottom left?  You should be able to, and can then try to shrink it, but beware, windows needs plenty of empty space to be able to run properly.  However with only about 28GB used on that partition you should be OK to go half and half.

Again, I think it best to shrink a windows partition using windows if possible, but I will have to leave that to you, as I don't know if XP has the disk management of later versions.  Once you have shrunk the partition, boot to XP to check it is still OK, and if so go back to the Lubuntu installer, once more using "Something Else" and point it to the free space on sda.  You will see at the bottom of the Something Else page an option for bootloader installation, and the choice shown in your pic is correct, ie /dev/sda, the root of the disk, **NOT** to the Lubuntu partition eg /dev/sda2

---

