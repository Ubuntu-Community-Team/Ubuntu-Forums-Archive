---
title: "Raid 1 setup"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by MikeLeePIY on 2010-04-09
I just finished installing Ubuntu Desktop 9.10 i368. There is two physical hard drives in my the computer. The first drive has Ubuntu installed on it and the second hard drive  is empty. 

I'm trying to setup raid 1 using the first active hard drive and the second hard drive. 

Is there a gui program I can use to create and manage the raid? 

If not please provide the commands needed to configure a raid 1 after initial setup

---

### Post by oldfred on 2010-04-09
Please see this thread discussing raid on desktop.

[http://ubuntuforums.org/showthread.php?t=1448988&highlight=raid](http://ubuntuforums.org/showthread.php?t=1448988&highlight=raid)

I am not a fan of raid for desktop use. But one of the comments had a link to a howto and other suggestions on hardware you should use.

---

### Post by cbecker78 on 2010-04-09
I assume you might also want to look at this site:

[https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles](https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles)

The only place I've ever configured RAID from was the motherboard, and that was basically just to change from striped to mirrored following promts over the phone from our IT department - so I can't be of much help.

I still don't know what ridiculous person setup RAID 0 on that desktop.


Note: the help link is for server installation- don't know if you have the same options in a standard install, but i guess you could always just install the server w/o any services, then install X and apt-get all the packages you want.

---

