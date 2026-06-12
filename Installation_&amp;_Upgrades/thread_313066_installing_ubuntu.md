---
title: "installing ubuntu"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by mykle on 2006-12-05
I'm trying to install ubuntu desktop in a partition on my harddisk, and everything works fine until I'm using geparted to mount root and swap. I get the same message everytime, "there is no root partition". There is problably something very stupid I've not done... But I can't figure it out.

---

### Post by LucasLinard on 2006-12-05
You must create at least 2 partitions. One swap and another (root). at some point during the install process you should create these partitions and the the mount point for root at /

---

### Post by mykle on 2006-12-05
Thanks for answer, but when I tried to set the first partition as \, in the menu and the other one as swap it still says no root partition. So I don't know what's wrong ?

---

### Post by LucasLinard on 2006-12-05
it is "/", not "\".

---

### Post by mykle on 2006-12-05
Ok I've tried, but is it working no.
Here's the scenario, I've made 3 partitions 1 for windows, and 2 small ones. 19 gb and 2 gb for ubuntu.
I get to the point where you mount the partitions. And sets the 19 gb as / ( actually thats all I write, and maybe thats the problem ?) and sets the 2 gb to swap. Everthing is from the menu. And the message is "No root file system". 
Something is wrong, but what ?? Please help a newbie !!!

---

### Post by LucasLinard on 2006-12-05
could you take a screenshot and send me?

---

### Post by rsambuca on 2006-12-05
I assume your using the 6.10 edgy CD?  If so, there have been a lot of known problems with the installation portion not recognizing partitions etc.  Try this and it should work:

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by mykle on 2006-12-05
Yes this is what I do, see the shots.

---

### Post by rsambuca on 2006-12-05
If you follow the link from my last post you will have instructions on how to get around this.  Note, you will have to select the reformat options as well.

---

### Post by mykle on 2006-12-05
Thank you, i will give it a try. Otherwise, I just maybe use the prev. version of ubuntu.

---

### Post by rsambuca on 2006-12-05
Good luck, and let us know how it goes!

---

### Post by LucasLinard on 2006-12-05
Man, from the screenshot it looks like you created 3 ntfs partitions. It can't be done like this. You should create one ext3 partition for linux, and one linux-swap for use as swap memory. Delete the partitions yous created for linux and create new ones, but make sure that they are ext3 for / and linux-swap for swap memory.

---

### Post by LucasLinard on 2006-12-05
to be more clear. you created 2 partitions, but they are in a wrong file system. you must use a linux file system. (ext3 for example)

---

### Post by Radiera on 2006-12-05
hda5 has to be primary if you want to boot from it

---

### Post by rsambuca on 2006-12-05
As long as you select reformat prior to installing, it will make the correct file systems.

---

