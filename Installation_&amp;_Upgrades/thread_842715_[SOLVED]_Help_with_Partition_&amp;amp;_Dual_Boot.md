---
title: "[SOLVED] Help with Partition &amp;amp; Dual Boot"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by DualJazz on 2008-06-27
<Moved from General Help>

Hello everyone!

I am slightly new to Linux but the only task ive done with Linux is install Debian Etch on another pc. So ive had no other proper skill in Linux.

Anyway, I have recently got Ubuntu Hardy Heron 8.04 Live DVD. I also have Windows XP on my computer too!

I wish to dual boot these two together and I understand you need GRUB to dual boot the two!.

Though i cannot do any of this due to partitioning! Currently my SATA hard drive is 1 whole partition containing everything i have on windows. Though, to get linux installed i need to make a new partition containing if im correct ext3 formatting and a small SWAP file.

I tried firstly the Ubuntu Live DVD with Gparted on the DVD. Though when resisizing the overall partition it came up with
"An Error Occured" with information about cannot write to the disk or something similar. So then I tried Gparted and i could change the partitions, but when applying I gained the same error again as on the Ubuntu DVD.

So overall I am stuck! So i need help from you great guys at Ubuntu forums to help me install and dual boot Linux and XP. Also if ive given any wrong info like the format type please say as this will correct me later on!

System - Core 2 Duo E4500, 2GB DDR2 Ram, 150GB HardDrive (104GB Left)

Any ideas are welcome! Thank you!

EDIT : My SATA is formatted as NTFS!

---

### Post by housam on 2008-06-27
Boot from the live cd and type the following code in the terminal ( applications >> accessories >> terminal ) and post the results :
```
sudo fdisk -l 
```
where -l is the lower case of L . 
Also post a screen shot of Gparted ( applications >> accessories >> screen shot )

---

### Post by DualJazz on 2008-06-27
Do u mean boot from Gparted or Ubuntu Live CD? And do i make the ext3 and swap extended?

---

### Post by pytheas22 on 2008-06-27
Sometimes, especially if your Windows install has been there for a while, it's impossible to resize the NTFS partition.  It sounds like this is what's happening for you.

There are some things you could do to try harder to make the partition editing work, but I think a better option would be to use [wubi]("http://wubi-installer.org/").  It will let you install Ubuntu "inside" Windows.  You don't have to deal with any repartioning, but you get a dual-boot system that runs Ubuntu exactly the same as an installation created using the traditional method.

---

### Post by DualJazz on 2008-06-27
So wubi will have all of Ubuntu installed then? So its Ubuntu inside windows?

And yes i agree i think its impoosible to resize with windows :)

---

### Post by DualJazz on 2008-06-27
Ill try gparted first! Ill post my results!

---

### Post by housam on 2008-06-27
> **DualJazz said:**
> Do u mean boot from Gparted or Ubuntu Live CD? And do i make the ext3 and swap extended?

I mean to boot from ubuntu live cd.
You need to create the two partitions using Gparted tool ( either from Gparted live cd or from ubuntu live cd )

---

### Post by Tom_ZeCat on 2008-06-27
Here's something else to consider.  Are you using a Desktop PC?  If so, do you have an expansion bay for another hard drive?  If that's the case, and if your budget allows it, you might consider using a second physical hard drive for Ubuntu.  That way both OSes have their own physical hard drives rather than logical ones, and, of course, you've got more room.  I did that with a dual boot Win 98/Win 2K computer and it paid off because when the drive containing Win 98 crashed, I was still able to boot up in Win 2K.  With logical hard drives, if your hard drive crashes, both OSes go down with it.

---

### Post by housam on 2008-06-27
> **DualJazz said:**
> So wubi will have all of Ubuntu installed then? So its Ubuntu inside windows?

And yes i agree i think its impoosible to resize with windows :)

windows partition can be easily resized using Gparted tool . but first you have to backup your data and to defrage the windows partition 2-3 times before resizing.

---

### Post by DualJazz on 2008-06-27
Okay im in the middle of the installation of ubuntu. I have entered into the terminal sudo fdisk -l , now it says the three options instead of four and its saying to use the full disk now. Problem is, i want to keep windows still!

Does this entire option get rid of windows? (I have backedup my important files so dont worry!)

Or what other option should i use?

Also will GRUB be installed during installation?

??

---

### Post by DualJazz on 2008-06-27
??

:)

---

### Post by housam on 2008-06-27
> **DualJazz said:**
> Okay im in the middle of the installation of ubuntu. I have entered into the terminal sudo fdisk -l , now it says the three options instead of four and its saying to use the full disk now. Problem is, i want to keep windows still!

Does this entire option get rid of windows? (I have backedup my important files so dont worry!)

Or what other option should i use?

Also will GRUB be installed during installation?

??
use the available free space option -
do not use the entire disk ( this'll damage wipe windows ).
grub will be installed by default during the installation.

---

### Post by DualJazz on 2008-06-27
I chose guided and now comes up with "This probablly happened because the selected disk or free space is too small to be automatically partitioned" On the topbar it says "Failed to Partition the selected disk"

help ?? :lolflag:

manual wont work either!

---

### Post by DualJazz on 2008-06-27
also cse my partititon is 1 whole, there is only 8mb unallocated space, is this a problem too?

If all else fails or cant be fixed, ill use wubi instead!

If any new ideas come up, ill still be glad to try!

And also can i still have some more room for windows as this is my common gaming OS

Ideas still?

---

### Post by DualJazz on 2008-06-27
Okay, im ending this thread now as i've found my way how to install Ubuntu now.

I would like to thank everyone who has helped and viewed this thread!

My solution was Wubi and cse im not a great linux user, im going to use this.

But once again thnx to everyone who has helped!
:popcorn:

Solution = Wubi

---

### Post by housam on 2008-06-27
> **DualJazz said:**
> also cse my partititon is 1 whole, there is only 8mb unallocated space, is this a problem too?

If all else fails or cant be fixed, ill use wubi instead!

If any new ideas come up, ill still be glad to try!

And also can i still have some more room for windows as this is my common gaming OS

Ideas still?

can you post the screen shot of Gparted image. just to know how much free space you've got on that disk.

in the worst case you still can install ubuntu inside windows using wubi.

---

