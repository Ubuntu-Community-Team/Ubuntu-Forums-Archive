---
title: "Ubuntu partitioning recommendations"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by Seiken on 2005-02-18
Hello,

I ran some searches on the forum and couldn't really find anything that pertained to my question. I am fairly new to linux. I am wondering what partition setup I should have before installing Ubuntu (I'm going with Hoary).

I have read in various places that, for linux in general, it is good to have your swap partition, a partition for /, one for home, and one for some other things. I would like to be able to try out other linux distros in the future and not have to lose the files in my home folder (and anything else that might be important). I just want to be able to format the / partition and install a new distro there when I feel like trying one.

Also, how do I go about mounting the home folder to a different partition?

Thanks,
Seiken

---

### Post by Xian on 2005-02-19
[QUOTE=Seiken]I have read in various places that, for linux in general, it is good to have your swap partition, a partition for /, one for home, and one for some other things. I would like to be able to try out other linux distros in the future and not have to lose the files in my home folder (and anything else that might be important). I just want to be able to format the / partition and install a new distro there when I feel like trying one.[/QUOTE]
You'll need the swap and / partitions no matter what else you decide, so just include those as a given. It sounds to me like your primary concern after that is to be able to keep your personal configs and home contents if you happen to install more distros. If you just add a /home partition this will do nicely. So basically you are just looking at a three partition set-up:

/
swap
/home

You can of course share your home partition with any other Linux installations.

---

### Post by Xian on 2005-02-19
[QUOTE=Seiken]Also, how do I go about mounting the home folder to a different partition?[/QUOTE]
Oh, and this is done when you get to the partitioning module in the Ubuntu installer. You will just select a given partition, and then you will have several options to choose from, such as whether or not to format the partition, what filesystem that it should use, and what the mount point should be named. There is a drop-down list that will include the "/home" selection.

---

### Post by jacob on 2005-02-19
I know next to nothing about LINUX but want to give it a try. I currently run win xp and have two physical disks installed (C and D) and keep my documents on D. I want to keep xp as a dual boot. I have partition magic so should be able to make additional partitions without too much damage! 

I assume the \ partition you refer to is the boot partition and shared with windows? and I have to make another partition on the C drive for the swap ?? 

any advice gratefully received.

---

### Post by dheerajmk on 2005-02-19
Hi jacob dheeraj here same problem as you any solution as yet 
please help me as soon as u get a solution!
i'll send you a gmail invitation if i can :-|

---

### Post by Xian on 2005-02-19
[QUOTE=jacob]I assume the \ partition you refer to is the boot partition and shared with windows? and I have to make another partition on the C drive for the swap ?? [/QUOTE]
The "/" partition is what is sometimes referred to as the Linux root directory. Now, the /boot directory will be installed to that partition unless you specify otherwise, but of course you can place that on a separate partition if you so desire. None of those are shared by windows as they only contain Linux specific data. You will and should make a partition for swap, but again this has nothing to do with the operation of Windows. It will only be used by Linux.

Don't let any of this get too complicated for you as most people just create a "/" and swap partition and then just use those for all required directories. In the end that is really all that you actually need and using only those Linux will install just fine. I've never set up a dual HD boot process, but there are many topics on that if you will search the forums.

---

### Post by dheerajmk on 2005-02-19
[QUOTE=Xian]The "/" partition is what is sometimes referred to as the Linux root directory. Now, the /boot directory will be installed to that partition unless you specify otherwise, but of course you can place that on a separate partition if you so desire. None of those are shared by windows as they only contain Linux specific data. You will and should make a partition for swap, but again this has nothing to do with the operation of Windows. It will only be used by Linux.

Don't let any of this get too complicated for you as most people just create a "/" and swap partition and then just use those for all required directories. In the end that is really all that you actually need and using only those Linux will install just fine. I've never set up a dual HD boot process, but there are many topics on that if you will search the forums.[/QUOTE]
  Hi please help me i have four partitions already
c:
d:
e:
f:
i want to install ubuntu on E: without losing any data on any of these partitions
also i already habe xp installed on D: and 98 installed on C:
please help i dont mind getting rid of 98

---

### Post by Xian on 2005-02-19
[QUOTE=dheerajmk]Hi please help me i have four partitions alreadyi want to install ubuntu on E: without losing any data on any of these partitions[/QUOTE]
I've never set up a dual-windows installation so I have really no idea of how to use those and boot to both of them. However, to install Linux you only need two new partitions, which would be the "/" and the swap partition. So, during the installation just create, format, and mount those and you should be fine. Linux will not write over any of your existing during the install so it is just a matter of getting the boot parameters correctly set.

It's honestly not that difficult. Try the installer and see how far you can get without stubbing your toe on something. If you get confused just don't write anything to disk and return to ask about the steps you found problematic.

---

### Post by dheerajmk on 2005-02-19
Thanks a lot dude 

 \\:D/

---

