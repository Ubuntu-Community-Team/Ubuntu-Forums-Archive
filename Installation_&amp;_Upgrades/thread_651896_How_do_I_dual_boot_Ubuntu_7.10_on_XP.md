---
title: "How do I dual boot Ubuntu 7.10 on XP?"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by sphere9 on 2007-12-28
How do I setup my computer to dual boot with Ubuntu 7.10 and are there any risks?

---

### Post by LaRoza on 2007-12-28
The menu for the install procedure has an option to resize your existing partition and install, simple and effective.

There is a slight risk, when altering partitions, so making backups, or restore disks is a good idea.

I have never had a problem.

---

### Post by sphere9 on 2007-12-28
so I don't need to create any partitions or anything?

---

### Post by forestpixie on 2007-12-28
the install does need a partition

that's what the resize does - it removes space from the existing partition and then uses that to make a partition 

and just to reiterate - make sure you have an effective backup

---

### Post by LaRoza on 2007-12-28
> **sphere9 said:**
> so I don't need to create any partitions or anything?

It will do it on its own. By default, it will create two partitions, one large one and one small one.

The resizer is a slider bar, the size you make it is the size of the existing partition, not the new one.

If it you move it to the left, you are shrinking the Windows partition, so don't go to far unless you want to.

---

### Post by sphere9 on 2007-12-28
so by making the windows one smaller i will be reducing the amount of space available to me for saving things with windows?

also how do i go about choosing whether or not to launch ubuntu or windows xp at start-up?

thankyou.

---

### Post by forestpixie on 2007-12-28
yep - resizing the partition emm.. resizes it ;) so you'll have less in the windows partition - but you should be able to access it from within gutsy 

once you've installed you should get a new menu at startup which will give you the choice of which you want to start with

you can later edit the menu in order that the one you prefer to start with is the default

---

### Post by LaRoza on 2007-12-28
> **sphere9 said:**
> so by making the windows one smaller i will be reducing the amount of space available to me for saving things with windows?

also how do i go about choosing whether or not to launch ubuntu or windows xp at start-up?

thankyou.

Yes. But you can always reconfigure later. I take time to set up my hard disks to maximize the use of space, but that might be a little complicated at first.

You'll see when you boot up. You get a menu, and can change the default.

---

### Post by Sef on 2007-12-28
You might want to read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by CypherHackz on 2007-12-28
slip in the ubuntu cd, choose installation. then when the already login in the ubuntu live cd, click on install icon. it is on the desktop. then follow the steps. when it comes to hd partitioning, choose manual so you can decide how to do the partitioning. make sure you have enough space for ubuntu. one partition for the system files and one partition for the swap. then proceed with the username and password. after that, install ubuntu. 

-cypher.

---

### Post by sphere9 on 2007-12-28
what can I do to prevent anything from going wrong?

and what could go wrong?

also, will ubuntu run faster than it does as a live cd?

---

### Post by SteveHillier on 2007-12-28
> **LaRoza said:**
> It will do it on its own. By default, it will create two partitions, one large one and one small one.

The resizer is a slider bar, the size you make it is the size of the existing partition, not the new one.

If it you move it to the left, you are shrinking the Windows partition, so don't go to far unless you want to.

The point to remember here is that if you shrink the Windows partition too much there is no room for Windows to grow.

---

### Post by SteveHillier on 2007-12-28
> **sphere9 said:**
> what can I do to prevent anything from going wrong?

and what could go wrong?

also, will ubuntu run faster than it does as a live cd?

*what can I do to prevent anything from going wrong?*  Become paranoid.  Backup (as suggested earlier).  Just make sure that everything that is important to you is tucked away on something removable.  You just never know.


*and what could go wrong?*  Who's law is it that says if something can possible go wrong then it will do!  A power cut halfway through resizing your partition will not give you a bundle of laughs.

*also, will ubuntu run faster than it does as a live cd?*  I don't know.  I expect so because it is quicker to retrieve data from HD than CD, but I have only ever used Live CD to do an install.

---

### Post by LaRoza on 2007-12-28
> **SteveHillier said:**
> 
*also, will ubuntu run faster than it does as a live cd?*  I don't know.  I expect so because it is quicker to retrieve data from HD than CD, but I have only ever used Live CD to do an install.

Yes, it will run much faster. 

The main issue with the live cd is that it has to read from an optical drive, which is much slower than a hard drive. Once it is loaded into RAM the program runs at normal speed. However, without a disk cache and slow access to load, speed and ability to run programs are reduced.

---

### Post by sphere9 on 2007-12-28
what about if somewhere down the line i want to uninstall ubuntu?

---

### Post by forestpixie on 2007-12-28
you'll need to reformat the partition to ntfs if you want windows to read it and then you'll need to redo the windows boot which you can achieve with the win disc - put it in a repair the mbr

all simply achieved - plenty of help here :)

---

### Post by LaRoza on 2007-12-28
> **sphere9 said:**
> what about if somewhere down the line i want to uninstall ubuntu?

The way I recommend:

Download the Super Grub Disk (see the link in my sig)

Burn and boot from it.

Use it to restore the Windows MBR: Advanced->Windows (Advanced)

Reboot the computer, Windows should load, with no sign of Ubuntu or Grub. Use the Windows Disk Management Tool to delete the Linux partitions and expand the Windows partition to fill the space.

---

### Post by sphere9 on 2007-12-28
so i assume using super grub is safe to use?

---

### Post by Romanus81 on 2007-12-28
I think you need to try Wubi. 
[http://wubi-installer.org/](http://wubi-installer.org/)
Wubi is how I got started on linux. You download the client (a .exe file) and open it in windows like any other program.
In a typical installation, you devide your hard drive into partitions and install linux on one of them, with wubi it creates a virtual disk (in C:/wubi) of a certain size as you specify in the installer, and places an entry in Window's boot list. You will be using Window's boot menu, not a GRUB, and when you turn on your machine, you choose ubuntu or windows. 
If you don't like it you can simply uninstall it like any other program.
Here is the ubuntuforums.org forum for it, if you need help.
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
The only downsides to wubi is that 1) Since the disk is virtual it can be prone to corruption if you do a hard power-off (hold down the shutdown button on your PC until it shuts off or if you unplug the PC) I never had any problems but make sure you let it properly shut down. Also it is slightly slower than typical ubuntu, although, I later partitioned my drive and didn't see any difference.

---

### Post by RockHaxor on 2007-12-28
Personally I  defrag Windows and then use Partition Magic to resize Windoze XP  ( this I believe is the safest way) and create the 3 other partitions I will need (home, swap and /).

Backing up your files is the best bet, I use an external hd to store my important data. I usually find myself reinstalling Windows every 6 months anyway (its like spring cleaning).

Just follow the prompts during install and you should have no trouble, if you run into a snag the help here is great.

---

### Post by sphere9 on 2007-12-28
thanks for all the help :)

however i am at the partition creating stage with the slider and wish to have roughly 20GB of my 107GB harddrive available to Ubuntu but the lowest I can choose is 40GB?

---

### Post by sphere9 on 2007-12-31
help? :/

---

### Post by forestpixie on 2007-12-31
I would be inclined to use one of the partition tools mentioned here - i personally find gparted fine

---

### Post by RockHaxor on 2007-12-31
Try partitioning prior to installation from the LiveCD.

System>Administration>Partition Manager (Gparted) As mentioned above it does a fine job>

---

### Post by forestpixie on 2007-12-31
although I use the livecd myself - tried the feisty version and haven't tried the gutsy one since then :)

---

### Post by wearekosh on 2008-01-01
look here - good dual boot instruction vid

[http://video.google.com.au/url?docid=-6104490811311898236&esrc=sr1&ev=v&len=811&q=dual%2Bboot%2Bxp%2Bubuntu&srcurl=http%3A%2F%2Fvideo.google.com.au%2Fvideoplay%3Fdocid%3D-6104490811311898236&vidurl=%2Fvideoplay%3Fdocid%3D-6104490811311898236%26q%3Ddual%2Bboot%2Bxp%2Bubuntu%26total%3D22%26start%3D0%26num%3D10%26so%3D0%26type%3Dsearch%26plindex%3D0&usg=AL29H20-tzwSVf_xt62b72ValZG9fMgAUA](http://video.google.com.au/url?docid=-6104490811311898236&esrc=sr1&ev=v&len=811&q=dual%2Bboot%2Bxp%2Bubuntu&srcurl=http%3A%2F%2Fvideo.google.com.au%2Fvideoplay%3Fdocid%3D-6104490811311898236&vidurl=%2Fvideoplay%3Fdocid%3D-6104490811311898236%26q%3Ddual%2Bboot%2Bxp%2Bubuntu%26total%3D22%26start%3D0%26num%3D10%26so%3D0%26type%3Dsearch%26plindex%3D0&usg=AL29H20-tzwSVf_xt62b72ValZG9fMgAUA)

---

