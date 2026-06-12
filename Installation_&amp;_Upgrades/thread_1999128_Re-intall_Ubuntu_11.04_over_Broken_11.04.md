---
title: "Re-intall Ubuntu 11.04 over Broken 11.04"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2012-06-07
Yesterday, I decided to start using Ubuntu 10.04 again. I was told it was no longer supported and that I should upgrade to 11.04. I did this, but I can't get 11.04 to run. I get the grub menu, but no amount of cajolling will get it to work.
 
I have a live CD for Ubuntu 11.04. How do I use this to re-install 11.04 or to get the existing version running. I have read the "sticky" at the beginning of this forum, but I find that I can't follow most of the advice.
 
Thanks for your help.

---

### Post by black veils on 2012-06-09
backup all your personal files, and any settings for specific apps, like your web browser and messenger.

you should use ubuntu 12.04, check the integrity of your ISO download, burn the disc at the slowest speed.

open **gparted**, then take a screenshot of it, and attach here with the paperclip.

i can say how to install once i see what it looks like.

---

### Post by vchapman on 2012-06-11
> **black veils said:**
> backup all your personal files, and any settings for specific apps, like your web browser and messenger.

you should use ubuntu 12.04, check the integrity of your ISO download, burn the disc at the slowest speed.

open **gparted**, then take a screenshot of it, and attach here with the paperclip.

i can say how to install once i see what it looks like.

Well I took matters into my own hands!

So I have installed 12.04 -- it works but the performance is not good.

I still have the broken 11.04. Can I get rid of this by using gparted and simply delete the partitions where it is installed.

Next question. How much swap space should be allocated. The install of 12.04 only allocated 2 gb. of swap space. 

Thanks for you help.

---

### Post by black veils on 2012-06-12
do you have Windows or any operating system you need?  you made a mess. you would be best just installing the 12.04 again, but choosing the option of erase entire disk, to format all that other rubbish away. but you need to backup all your files (personal data stuff).

swap needs to be the size of your ram, plus 100 mb, or your ram x 1.5. for example, if you had 2 gb ram, you would want 3 gb. there are 1024 mb in a gb.

about the performance, what is your ram? processer speed? harddrive size?  if you don't have enough comfortable speed, you could try Xubuntu, its low on resources but got plenty of options. and has panel options like gnome 2.

---

### Post by Bucky Ball on 2012-06-12
> **vchapman said:**
> Yesterday, I decided to start using Ubuntu 10.04 again. I was told it was no longer supported and that I should upgrade to 11.04.

Wrong. 10.04 LTS is supported until April 2013 and IMHO is the most stable release at this point. ;)

I'd install that. You might have a smoother ride (as has been around for long enough to have the bugs ironed out).

Whatever you install, choose 'Something Else' at the partitioning section and install only / (if you have a separate /home this will remain intact and automatically be used for /home in the new install, same with /swap, there should be one there already so you don't need to make it again).

---

