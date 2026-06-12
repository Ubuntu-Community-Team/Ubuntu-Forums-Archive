---
title: "Partioning Problems!"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by mjnichol on 2010-10-30
Hello, I just installed Windows 7 and then proceeded to install Ubuntu 10.10 within Windows 7 using the automatic installer. I created a new NTFS partition for the installation and it seems like it worked; however, after booting Ubuntu it seems that the drive it has been installed on only has an additional 2.6 MB of free space. I looked in the disk utility and it seems that it somehow made its own partition (a 2.9 GB Ext4 type). Is there any way I can acquire more space for this partition? If so, where is this partition even stored? 

I hope this is clear enough!

Thank you for the help!

---

### Post by wilee-nilee on 2010-10-30
So when you install Ubuntu inside of Windows you should not be creating an extra partition for it this can cause problems, although do-able.

Can you boot a live Ubuntu cd and take a screenshot of gparted or the disk manager in W7.

To be honest it is kind of hard to really tell what you have done, at least for me.;)

---

### Post by mjnichol on 2010-10-30
Hi again,

I cannot boot properly from a live CD unfortunately. I get an error which I could not resolve which is why I ended up doing the installation the way I did. Anyway, I took a screen cap of my partition configuration. Here it is!

---

### Post by wilee-nilee on 2010-10-30
When you installed wubi did you size the file for Ubuntu, and what size did you make it. 

The wubi install is a pseudo virtual setup it goes to a file not a partition, normally you would of just installed into the W7 C drive and chose the size of the file. By additionally partitioning you actually made it harder and more complex, which as it is wubi is as stable as the platform it is in at best. 

To be honest if you have a thumb you can load with Ubuntu I would get rid of the wubi and just do a standard dual boot. If you set it up this way you will have more control and a easier, fixable situation in the long run if you have problems with either OS. Much more stability overall.

---

### Post by mjnichol on 2010-10-30
I do have a thumb drive, so i think I will just do a boot from there. Thanks for the help.

---

### Post by wilee-nilee on 2010-10-30
> **mjnichol said:**
> I do have a thumb drive, so i think I will just do a boot from there. Thanks for the help.

If you need any help with it just ask, lots of people on here to help out.

From looking at the screenshot it looks like if you make sure nothing but wubi was in F you can just remove it. You would then have two unallocated spaces. The ubuntu installer will auto install and set you up in a unallocated space just be sure to have it pointed at the correct free space you want filled.

Just to be safe I would remove wubi first by opening the folder there is a removal link there.

---

### Post by mjnichol on 2010-10-30
Got the thumb drive prepared and cleared the partition out. I will install later tonight. Thanks for the help!

---

