---
title: "Installer Options For Separate /Home Partition"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by MARP1961 on 2012-03-16
Does anyone out there agree that the Ubuntu installer should include an option for setting up a separate** /Home **partition? 

I know that this is easy to set up manually under the **'Do Something Else' **option; but for beginners I think that perhaps the default installation should include this as a useful feature.

---

### Post by sandesh.sboa on 2012-03-16
Hey im a beginner and I would like to know how to install with The option you mentioned. I have a empty 20 gb partition in my Hard disk formatted in the ntfs format but when I use this option it is not shown separately but combined with my rest of the drives and I get a option as a whole chunk of 350 gb of my 750 gn hard disk. Can u help me out in this ??  


Thanks

---

### Post by MARP1961 on 2012-03-16
I assume you want your main hard drive to just have Ubuntu and no Windows? If this is the case and you want a separate /Home partition proceed thus with three partitions (primary or logical):


[LIST]
[*] Boot from install CD or USB (I recommend Ubuntu 11.10), allow it to load and choose 'Install Ubuntu'.
[/LIST]

[LIST]
[*]Select the install option of** 'Do Something Else'.**
[*]You can now click on each partition and delete it to clear your drive of any old partitions. Make sure you have copied any important files you might want to keep onto other storage media before you do this!!
[*]If you then click the green tick to apply these changes you will see your hard drive as **Unallocated Space.**
[*]You can now create your own partitions by clicking **New.**
[*]You need about 15GB (that's ample) for Ubuntu system. Do this by setting the size, choose** ext4 journaling file system** and set the **mount point** to** /** at the beginning.
[*]I then set a **Swap **partition which is needed as memory. This needs to be about twice your RAM in size (for me this is 4GB). The Swap does not need a mount point but I place it at the end for 'tidiness'.
[*]The remaining space can then be set up for 'Home'. Click **ext4 journaling file system** and set the** mount point** to the **/Home** option from the dropdown menu.
[/LIST]
You are then set to apply these changes. You can go back at any stage and alter things until you reach this final step. Once happy then allow it to install.


In the future, with a Home Partition, you will be able to reinstall Ubuntu easily by disk or USB by going back to the manual install option described above but remembering that once you have settings and files you want to keep you will need to mount your 'old' Home Partition again as /Home but on that occasion you will need to make sure the** Format** box is **not checked**. 


Finally a warning: Whenever you do anything with partitions or reinstalling you should **always** back up important data and files onto external storage. Even though your Home Partition allows you to 'cheat', there is always the slight risk something will go wrong or you erase or format the wrong partition. Good luck and ask for specific help if you get stuck.

---

### Post by darkod on 2012-03-16
> **sandesh.sboa said:**
> Hey im a beginner and I would like to know how to install with The option you mentioned. I have a empty 20 gb partition in my Hard disk formatted in the ntfs format but when I use this option it is not shown separately but combined with my rest of the drives and I get a option as a whole chunk of 350 gb of my 750 gn hard disk. Can u help me out in this ??  


Thanks

Just to clarify on top of what has already been said above. Linux doesn't install on ntfs so you will have to delete that ntfs partition and leave it as unallocated space.

Also, if 20GB is all you have got for the full ubuntu install, having a separate /home might be difficult. Yes, you can install, but that will not leave much space for /home if you use 15GB for root and plus something for swap. Even if you bring root down to 10GB that still doesn't leave much for /home.

Think about it and about how much space you will like to use for ubuntu.

---

