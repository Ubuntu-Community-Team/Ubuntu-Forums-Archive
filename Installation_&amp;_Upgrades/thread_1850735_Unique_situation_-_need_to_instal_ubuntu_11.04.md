---
title: "Unique situation - need to instal ubuntu 11.04"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by rishi_singh on 2011-09-27
Here is what i did so far. Put ubuntu 10.04 alongside win 7. Restored mbr of win 7. Then went to disc management of win 7 and deleted the partition of 40gb for ubuntu. Then "re created" the partition. I was not very confident about what i was doing. Now the 40gb appears in win 7.

I want to : 
(1) Instal ubuntu 11.04 in that 40gb free partition. I cannot and i see some drives listed in installation of ubuntu. But i get some options like ext3, ntfs, swap etc on small window when i click on the 40gb partition. It also shows options like revert, change etc. I dont understand these things.

(2) Be able to choose which OS i boot into.

(3) Want my win 7 to be hidden from linux. I DONT want to be able to access win 7 partition from ubuntu.

Please help me to do this.

---

### Post by Blasphemist on 2011-09-27
So lets work on 1 and 2 first. And by the way, I do expect this to be merged with your other thread by a moderator. 

The easiest thing for you to do is this. Use the same tool you used in windows to create the new partition for ubuntu to delete it. You will then have that space un-allocated. The boot into the ubuntu installation and you will have an option to install in the un-allocated space. Choose that and you won't have to make partition decisions. When asked where to install the boot loader, install it to sda where a is the first hard drive. If you have more than one hard disk, choose the drive you are installing ubuntu to but it sounds like you just have one drive. 

Doing this will give you a dual boot installation of windows and ubuntu with Grub2 as the boot loader that will give you the choice of which to run. Do install with a wired connection to the internet. After the install, go into the additional drivers application and see if there is a driver listed for your wifi. If so choose to install it and re-boot. Then install all updates and you are good to go.

---

### Post by rishi_singh on 2011-09-27
Ok, i will show the screen during installation that i cant understand. How do i post pics of that here ? BTW i have no idea of what partitions really are. I just know the english meaning. I dont know how all that ntfs, fat, mount, unmount, allocate is. Its all jargon to me. I get the sinking feeling that this is going to be a computer science course.

Please look at the article below. That is what i am trying to do. The article is not exactly as per my situation, So i dont want to end up selecting the wrong options and messing things.

[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

I want guidelines similar to the article above.

---

### Post by rishi_singh on 2011-09-27
Never mind. Did it myself. Win 7 recovery disc - command prompt -  bootrec /fixmbr - go to windows - prepare old partition - instal ubuntu  11.04 - use ext3 journalizing bull-poop - done.

What those steps mean, i dont understand. But it got the job done. A few  more hours in linux and i can declare myself a phd in computer science.

---

