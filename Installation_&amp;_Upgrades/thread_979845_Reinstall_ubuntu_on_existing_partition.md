---
title: "Reinstall ubuntu on existing partition"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by ghanagareth on 2008-11-12
I have ubuntu on an existing partition, however I would like to reinstall ubuntu again on the existing partition.  So how do I uninstall the existing version, and then reinstall ubuntu again on that same partition?

---

### Post by tuxxy on 2008-11-12
Boot the install CD as normal and select that partition you want to use at the partitioning stage of the install, also be best to move you /home to seperate partition first if you need to save current files/settings

---

### Post by ghanagareth on 2008-11-12
I have an existing ubuntu partition, but I would like to uninstall ubuntu and then reinstall it in the existing patition.  Does anyone know how to do this?

---

### Post by ghanagareth on 2008-11-12
Hi Tuxxy:

If I dont uninstall ubuntu and then try to install it in the ubuntu partition, will this delete the existing version and replace it with the freshly installed one?

---

### Post by Kevin Fischer on 2008-11-12
You don't need to uninstall Ubuntu, just run the install off the CD as usual.

1) When you get to the dialog asking you which partition to install Ubuntu on, choose Manual.
2) Select your Ubuntu partition from the list and set its mount point to '/' (it's on the dropdown menu). Check the format box.
3) Select the swap partition from the list and set it as swap.

If your Ubuntu install is on multiple partitions, you will need to do the same for them, but if you did the default install don't worry about this step.

---

### Post by oilchangeguy on 2008-11-12
why do you have two threads on the same subject?
[http://ubuntuforums.org/showthread.php?t=979854](http://ubuntuforums.org/showthread.php?t=979854)
can a mod please merge these threads?

---

### Post by ghanagareth on 2008-11-12
Hi Kevin, 

Will this the cleanly remove my older version of ubuntu, removing all previous settings and information (which is what I want)?

Thanks a lot for you help!

---

### Post by overdrank on 2008-11-12
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by ghanagareth on 2008-11-12
So will a new install over the old ubuntu delete everything from the older one first, including settings?

---

### Post by m_l17 on 2008-11-12
> **ghanagareth said:**
> So will a new install over the old ubuntu delete everything from the older one first, including settings?

Yes, you can also at reinstall time format the partition. Make sure you save your /home or files that are important to you.

---

