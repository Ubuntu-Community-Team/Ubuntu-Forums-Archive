---
title: "install win 8 with ubuntu"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by tyrone.clarke on 2013-11-20
Hey guys

New here and sorry if this has been discussed 

I have a laptop that has ubuntu 13.04 install as the os and for work I need windows 8 for certain programs

What im needing to know is how would I go doing a dual boot? I have alot of data etc that I have on the hdd and cant afford to lose but havent got a external hdd to transfer too. 

Am I able to install windows 8 and then install ubuntu but some how save the data thats in the home folder and downloads folder? 

Ive tried running windows with virtual box but rather have the option to choose what os I want when booting up the pc

Sorry for being a noob

Thank you guys

Ty

Ive used vine as well but would like to dual boot if possible

---

### Post by Bucky Ball on 2013-11-20
Open Gparted and take a screenshot of it showing how your machine is currently set up. Attach the screenshot to your next post.

---

### Post by tyrone.clarke on 2013-11-20
this is the screenshot here i havent changed anything since i got the laptop a few weeks ago

---

### Post by Bucky Ball on 2013-11-20
Okay, right click on your /home folder and see how big that is. That is how much you are going to need shrink sda1 and expand sda2. You need to do this by booting from the LiveCD and using Gparted with all partitions unmounted (you can't do it in a running install).

When you've done that, create a logical drive in the extended partition with the free space you've now created and put your data from the /home folder into that.

Now you will have a heap of free space in sda1. Shrink that from the beginning, not end, so you leave, say a 40Gb partition for Windows at the BEGINNING of the drive. Leave that free space and install Windows to that (will create a primary partition at the beginning of the drive).

You are probably going to need to do a bit of fiddling to get the boot up and running, but that's basically it. 

How much data do you want to get off the /home partition (in Gbs)?

PS: This is the perfect example of why it pays to have a separate /home partition. ;)

---

### Post by tyrone.clarke on 2013-11-20
awesome thank you

ill try that all out when i finish work!

thanks for your help and ill post how it goes

---

### Post by Bucky Ball on 2013-11-20
All good. Just let us know if you get stuck.

Main thing to remember is Win needs to be on a primary partition (Ubuntu doesn't care) and it plays nicest if on the first partition. With any luck, you will only need to run:

```
sudo update-grub
```

... in the Ubuntu install when all done and that should pick up the Win install and all good. As I say, with any luck. ;)

---

### Post by oldfred on 2013-11-20
I have not moved partitions for ages.
Does gparted now let you shrink from the left?
It used to be a two step process to shrink from right and then move entire partition right?

---

### Post by Bucky Ball on 2013-11-20
Shrink any direction you want. ;)

Could shrink sda1 from the left straight up but should move personal data onto another partition before attempting.

---

