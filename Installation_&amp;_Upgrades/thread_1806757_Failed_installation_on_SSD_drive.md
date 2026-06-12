---
title: "Failed installation on SSD drive"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by Yegor on 2011-07-18
Hi there,

I tried to install Ubuntu 10.04.2 on my new SSD drive. Installation processes up to 25% copying files and stops with Error 30: Read/Write error to hard disk. If I try to install Ubuntu 11.04 it even does not recognize new hard disk.
Motherboard: ASUS M4N68T-M. 
Drive: OCZ Agility 2 60Gb.
Searching result: possibly it could be problem with AHCI driver. I did not find any option about it in my BIOS but technical documentation says that my motherboard support AHCI by default. During installation Ubuntu uses sata_nv driver. How could I process installation using AHCI driver?

---

### Post by ajgreeny on 2011-07-18
[QUOTE]Motherboard: ASUS M4N68T-M. 
[COLOR=Red]Drive: OCZ Agility 2 60Gb.[[/COLOR]/QUOTE]
I think the 2.6GB is the problem.  It's far too small for ubuntu; you need probably 5GB minimum.

EDIT:  Sorry, I think I misread your post.  Is it a 60GB drive?  If so I can not help you.

---

### Post by Yegor on 2011-07-18
> **ajgreeny said:**
> 
I think the 2.6GB is the problem.  It's far too small for ubuntu; you need probably 5GB minimum.

EDIT:  Sorry, I think I misread your post.  Is it a 60GB drive?  If so I can not help you.

yes, it's 60Gb. :) However, thank you for quick answer.

---

### Post by Yegor on 2011-07-20
Any ideas?

---

### Post by oldfred on 2011-07-20
My motherboard supports AHCI but in BIOS is have to enable it. Are you sure there is not a setting somewhere in BIOS?

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by marchar on 2011-07-20
I have a Corsair SSD F60 with the same problem.  At first only the BIOS would recognize the SSD, but it was not recognized in the installed Ubuntu 11.04 (on other HDD that I am trying to replace) in GParted etc. and also NOT in the Ubuntu 11.04 install CD when I tried to install Ubuntu on the SSD.  Corsair suggests that a shorter SATA cable (as short as possible) might help.  Other than that suggestion, they have been no help. In my case, the SSD responded a little better with the 8" cable, but all attempts to install 11.04 fail at the partitioning stage of the installer CD where it shows a "bad drive" message.  The installer does manage to put in the Swap partition, however.  

Searching the Net, it appears that this issue of non-recognition is not uncommon with Ubuntu & other Linux distros, but no clear solution has shown up.  It almost seems that the SATA controller's signals are too hit and miss or weak to let the SSD work with large writes of data.

The SSD does seem to work as a data drive, however, so am testing this with NTFS file format to see if it will be stable enough to trust data with it.

Pretty disappointing.](*,)

---

### Post by pqwoerituytrueiwoq on 2011-07-20
check its SMART status
if you put a ext4 on it be sure to mount it using the noatime and nodiratime options to reduce ware
i setup my install on my 16 gb ssd by copying via gparted

---

### Post by marchar on 2011-07-21
The SMART status is OK with this SSD.  Reads and writes, in ext4 but unable to install 11.04 OS even though it is recognized by the installer CD.  Using NTFS now as test to be able to use as data drive for dual boot Win7...... which is a waste of the SSD!  Hopefully, a solution will show up and I can install Ubuntu 11.04 on the SSD as planned.

---

### Post by Yegor on 2011-07-22
> **oldfred said:**
> My motherboard supports AHCI but in BIOS is have to enable it. Are you sure there is not a setting somewhere in BIOS?

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

I searched enough, but did not find that option in BIOS. Only option for IDE Controller.

---

### Post by Yegor on 2011-07-22
Will try to install Ubuntu 10.04.2 today once again. Ubuntu 11.04 still does not recognized hard disk. :( SMART displays that everything is OK.

---

### Post by pqwoerituytrueiwoq on 2011-07-22
is there a partition table on the ssd? with out a table you can't make a partition

---

### Post by Yegor on 2011-07-24
Yes,
Partition table was created (tried both MBR and DPT). Tested a lot of combinations of BIOS options and distributives. I even tried copy partitions from my old drive to the new one. Copied without errors, but boot from new drive was failed.
Will try to install windows or MacOS tomorrow. Also will try to run it on another motherboard...
Interesting, could SSD work without AHCI option?

---

### Post by Yegor on 2011-07-26
I tried to install Windows 7 on my new SSD yesterday and everything looks OK. Windows recognized it correct and installed without any additional questions. Also I did not make any changes in BIOS.
Anybody had issues with installation Ubuntu on SSD?

---

### Post by Yegor on 2011-07-28
any ideas?

---

### Post by steve11911 on 2011-07-29
There is strong evidence that Ubuntu will install on these drives.Please consider the pages linked below:

[http://www.matrix44.net/cms/notes/gnulinux/ubuntu-11-04-and-ssds](http://www.matrix44.net/cms/notes/gnulinux/ubuntu-11-04-and-ssds)

A good basic info page from the ozctechnology forum. I'd look closely starting at page 26 and suggest a careful bios settings review-just to be sure. 

[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567557&viewfull=1#post567557](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567557&viewfull=1#post567557)

Once installed this page is noteworthy and posts some impressive benchmarks:

[http://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu](http://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu)

---

### Post by marchar on 2011-07-31
Steve...
Your link is broken...

[http://www.matrix44.net/cms/notes/gn...11-04-and-ssds](http://www.matrix44.net/cms/notes/gn...11-04-and-ssds)

Can you please correct and re-post?

Thanks!

---

### Post by steve11911 on 2011-07-31
I apologize for your inconvenience.The link was good when posted.How disappointing to have such a timely page pulled.Fortunately,the cached page is still around:

[http://webcache.googleusercontent.com/search?q=cache:KtQPq4jMrTAJ:www.matrix44.net/cms/notes/gnulinux/ubuntu-11-04-and-ssds+ubuntu+11.04+on+ssd&cd=8&hl=en&ct=clnk&gl=us&source=www.google.com](http://webcache.googleusercontent.com/search?q=cache:KtQPq4jMrTAJ:www.matrix44.net/cms/notes/gnulinux/ubuntu-11-04-and-ssds+ubuntu+11.04+on+ssd&cd=8&hl=en&ct=clnk&gl=us&source=www.google.com)

(brief pause to reflect on appreciation of cut and paste)

and a bonus:

[http://www.bitsbythepound.com/using-a-solid-state-drive-ssd-with-ubuntu-11-04-409.html](http://www.bitsbythepound.com/using-a-solid-state-drive-ssd-with-ubuntu-11-04-409.html)

---

### Post by marchar on 2011-10-28
28 October 2011:I have the Corsair SSD F60 mentioned above and have done everything imaginable to get it to accept an installation of Ubuntu.  Finally, Corsair replaced the drive, so today I got to try it again.  Decided to go with 10.04 LTS for stability.  The SSD was recognized and the install started.... but hung at 15 minutes.  Just won't work for X reasons...  So, beware....:(:(

---

