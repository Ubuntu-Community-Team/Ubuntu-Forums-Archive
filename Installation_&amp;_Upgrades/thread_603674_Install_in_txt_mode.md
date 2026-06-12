---
title: "Install in txt mode"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by kkmc92 on 2007-11-05
Does any one know a good walkthrough or have directions for installing 7.10 in text mode?   ** HELP**!!

---

### Post by phrostbyte on 2007-11-05
It really shouldn't be that difficult to figure out without a manual. If you do need a mnaual check out [http://help.ubuntu.com](http://help.ubuntu.com) and search for a installation guide

---

### Post by infinitezero on 2007-11-05
Check out this link, it is for 7.04, but will work the same for 7.10.

[http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html)


iz

---

### Post by kkmc92 on 2007-11-05
> **phrostbyte said:**
> It really shouldn't be that difficult to figure out without a manual. If you do need a mnaual check out [http://help.ubuntu.com](http://help.ubuntu.com) and search for a installation guide

My problem is when I get past the key board selection and driver setup it comes to somthing about partitioning. I am not a commputer programmer so I don't really know what to do. That link is for 7.04 installation by the way.

---

### Post by infinitezero on 2007-11-05
kkmc92,
The text install of the two version are the same. If you are using the entire hard drive, just choose 
Guide - use entire disk

It will then show the disk or disks (if you have more than one), select the correct disk. It will ask you then to verify that you really want to format, select yes.

If you are doing a dual boot from the same hard drive check out the link below it does a good job of explaining partitioning.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

iz

---

### Post by kkmc92 on 2007-11-05
> **infinitezero said:**
> kkmc92,
The text install of the two version are the same. If you are using the entire hard drive, just choose 
Guide - use entire disk

It will then show the disk or disks (if you have more than one), select the correct disk. It will ask you then to verify that you really want to format, select yes.

If you are doing a dual boot from the same hard drive check out the link below it does a good job of explaining partitioning.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

iz

Thanks a bunch dude!!

---

### Post by infinitezero on 2007-11-05
No problem, I hope it goes well for you. I switch to Linux 2 years ago and have not looked back since. Just remember there is a little bit of a learning curve.


iz

---

### Post by zvacet on 2007-11-05
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by kkmc92 on 2007-11-05
Okay thanks for all the help! When I start the text install it goes fine untill it comes to the partitioner. In the walkthrough [http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html) it shows this screen.
[img] http://www.ubuntugeek.com/images/lamp/2.png[/img]


The screen that is on mine is different. It has three options to highlight and select. They are: 
** Help on partitioning**
** Undo changes to partitions **
** Finishing partitioning and wright changes to disk**

Does any one know what I should do now?????   ** PLEASE HELP **

---

### Post by phrostbyte on 2007-11-05
Finish partition and write changes to disk

---

### Post by kkmc92 on 2007-11-06
> **phrostbyte said:**
> Finish partition and write changes to disk

Thanks for your response. When I highlight that and press enter it displays a screen with a red backround saying:

                                 ** !! **    ** Partition Disks **
                               
                                  [color=blue]  No Root File System [/color]

                            ** No Root File System Is Defined **

                               ** Please correct this From The Partitioning Menu **


** < Go Back> **                                                                        ** < Cotinue> **


When I press ** cotinue** it takes me back to the ** partitioning menu **
Any more ideas???????

---

### Post by zvacet on 2007-11-07
Try with **Help on partitioning** and if that doesn´t help you to see on screen what you show as in your post,please chek disc for errors and do the md5 sum chek.You must be able to come to that point of installing,because withot it you can not go ahead.

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

You will find on this page everything about burning and cheking.

---

