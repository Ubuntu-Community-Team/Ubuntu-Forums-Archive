---
title: "Initial Install Problems for Dual Booting with OS X"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by jderosa3 on 2006-12-04
I would like to welcome myself to the group and hope to have a long stay as well - I wish my first post would be something to add to the community but I am new at all this, but a quick learner...

I know my question has been asked quite a bit, but I am still having issues - I am going to be as detailed as possible to try and get this answered.

**My Goal:**

*To dual boot OS X Server and Ubuntu 6.10 on my Powerbook G4 with OS X as the defaul system to load with yaboot.*

**My Hardware:**

*Powerbook G4, 1024MB RAM, 80GB HDD*


I have tried this 3 times with outcomes ranging from my current OS X install being replaced by Ubuntu to trying to install onto another partition and the installer telling em that there is no boot partition. I have tried using the ext3, hfs and fat32 filessystems, but I truly think I am missing a step... ](*,) 

I currently went back to square 1... I needed to get my laptop running with OSX so I did the following:


made two partitions 1 x 70GB partition using HFS (journaling disabled) for my OS X install and 1 x 10GB partition using HFS (journaling disabled) for the Ubuntu install when I can firgure this out.


I would like to install Ubuntu on the 10GB partition without touching the OS X partition.

I know there are 3 options when I am ready to install.


[B]1) use the whole drive on IDE1 (my hdd) this obviously erases everything - I don't want that.

2) Is to use the most contiguous (spelling? sorry) free space - I don't think this option is for me  with the situtation I want.

3) Edit partitions - is this where I need to be [/B]:-k 


I am assuming it is possible to do this - there are people that are dual booting on a mac...

Just to clarify I am running the PowerPC version of ubuntu 6.10 and it loads perfectly fine on the CD... Just having issues getting it up and running...

I apologize once again for this newbie question again, but I really am trying here.

Thanks for any replies in advance!

---

### Post by jderosa3 on 2006-12-04
I found the following page:

[http://trainque.com/blog/2006/10/21/how-to-dual-boot-ubuntu-osx/](http://trainque.com/blog/2006/10/21/how-to-dual-boot-ubuntu-osx/)

this is a paragraph from this tutorial:

When you get to the question about how you want to install Ubuntu, Be sure to check the box marked “use largest continuous free space”. This is very important. If you check something else, you risk losing your OSX partition.

In my case above I only set 10 GB aside - will that be enough to have this option work for me...

Please let me know - thanks!

---

### Post by jderosa3 on 2006-12-05
I figured it out and it is working smoothly!!!

I will post my findings later incase someone needs them - Give me a bit to do a writeup...

---

