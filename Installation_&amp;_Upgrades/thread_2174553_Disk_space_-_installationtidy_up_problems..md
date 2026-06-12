---
title: "Disk space - installation/tidy up problems."
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by GSD4ME on 2013-09-15
Can someone please help me?


I have run into some sort of non-minortrouble with my Ubuntu installation


The update manager informed me a fewweeks' ago that I had updates to do, so I started them off.


All completed but one did not – Ithought nothing of it but over the next few days the update managerkept telling me that this update was required to be done– so I haveseveral times attempted to install it, all to no avail: it keptfailing to install for some reason, which again was not reallyworrying me.


After a while, I found some time toinvestigate and am now confused and worried.


After investigations, it turns out thatthis package cannot be installed because the “disk is full” -several people have noted this 'error' on the forum and theexplanation was that it wasn't the actual device that was full butthe nodes concerning files. The advise was to delete some files andsee if this improved things. Also recommended was un-installation ofsome packages via differing routes, using terminal interfaces and/orsome packages designed to help out with installation problems.


However, this is where things getmessy.


I have tried to remove the variouspackages via different methods, as per explanations on the forum andon some web pages, but the removal of some packages fails because itcannot create a temporary file due to – yes, you guessed – lackof disk space.


I have tried to create space by erasingsome files and completely clearing my browser history but this is notmaking any difference. Part of the trouble is that I am unsure aboutLinux – I am a relative newbie of Ubuntu (from Windows) and amdesperately trying not to lose all of my files and data!


The 'disk' that is failing is apartition of file type ext4 that I created on my dual-boot machine tohold the Linux system – it is 5GB in size, which I was assuredwould be ample for an installation.


I have also played around at looking atthe disk area that I THINK is relevant to my machine:
>File System>usr>src


where there are many folders of theform 
linux-headers-3.2.0-yy
linux-headers-3.2.0-yy-generic
linux-headers-3.2.0-yy-generic-pae


where “yy” goes from 29 to 45 on mymachine. In this src folder there are 613,150 files taking up 1.6Gbof space.


Q: Are these files needed? What arethey? If they are not required, how do I get rid of them –remembering that I cannot do anything due to 'lack of space' on thedisk? Can I simply delete them? I am of the opinion that they existso that people can adapt their own system to be what they want – ineffect, the open source feature of Linux.


Failing this route, can anyone help mehere as I am becoming a bit paranoid about my system? I do not wantto foul up my machine to the point where I lose a life-time of data(suicide anyone?) and I want to be able to install a couple ofpackages that I require – including GPARTED so that I don't have toworry about a lot of this stuff again!


I am unable to install or remove anypackages nor clean up my system at all/easily – any help would bemost appreciated.

---

### Post by ibjsb4 on 2013-09-15
> The 'disk' that is failing is apartition of file type ext4 that I  created on my dual-boot machine tohold the Linux system &#8211; it is 5GB in  size, which I was assuredwould be ample for an installation.

You need to get your money back on that one.  5G, as you have found out is not enough.  Since this is a fresh install I would think it would be easier just to start over again.  A complete reinstall.

---

### Post by grahammechanical on 2013-09-15
The Linux kernel is developed independently to Ubuntu. Whenever the kernel developers update the kernel with various fixes the Ubuntu developers push it to the user through the Update system. The old kernels are not removed. There is sense to this. If the new kernel breaks the system we can boot into a previous kernel and get a working system. We see these kernels in the Grub boot menu.

The Linux developers have not provided an automatic removal of old kernels method. I think that you are using Ubuntu 12.04. If so you may have Synaptic Package Manager installed. So, no need to download another application which you cannot do due to lack of disk space.

Make a note of the last two kernels. You will want to keep them. Make a separate note of the names of the other kernels. You will want to delete them. Open Synapic Package Manager and search for Linux or Linux image. Items with a green icon are installed packages. Look for installed Linux images that are on your to be removed list, select them and right click and select Mark for Complete Removal. You will see things like Linux-image-generic, linux-image-extras, linux-headers. Each of them will have a version number. So, you can identify the oldest from the newest. That is how you can remove these Linux images and create more space.

There is another thing that you can try. I have never done it. So, I do not know how effective it will be. At the Grub boot menu select Recovery Mode. At the Recovery Menu select Clean - Try to Make Free Space. That will run a script that calls two commands - apt-get clean and apt-get autoremove. They will identify packages that you do not need and remove them. This is something you can do without installing any extra applications to clean up. It may even remove old kernel images.

Regards.

---

### Post by col48 on 2013-09-15
To avoid losing a life-time of data, copy all your data to _somewhere offline_ - memory stick, removable hard drive, whatever.
Do it again, so you have two independent clean copies on different media, and check you can read the files on both.
If you might be paranoid, do it a third time.

If this is a significant amount of data (in my case this would be many more than the 5Gb you have in total!), delete the data on the computer.
Now let it complete the update.
Assuming it now succeeds, compare the amount of free space with how big your now-offline data is.
What you do now depends on what you discover.  Do you buy more disk capacity, replace a failing disk, reorganise the partitions, just copy your data back, etc etc?
Personally, I'd want to be sure I'd never need to use more than 80% of the free space for my data, but that's up to you.

---

### Post by GSD4ME on 2013-09-25
Apologies for not getting back sooner - been on jury service

Many thanks to the posting people - grahammechanical was the most helpful and I carried out what he said to try and am now able to at least have some space in the disk partition to now tidy up the area.

Agree that the developers of linux/ubuntu need to have a method of tidying up 'old' installations rather than just leave them lying around.

BTW - no-one answered my query about the sources on the disk - see my original post - is it safe for me to delete these files?

many thanks again

---

