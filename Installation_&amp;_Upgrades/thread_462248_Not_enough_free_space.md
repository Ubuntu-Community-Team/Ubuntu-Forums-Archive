---
title: "Not enough free space?"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by Asian_Wannabe on 2007-06-02
In a previous post I could not get past the partitioning step of installing ubuntu. I want to have xp and ubuntu on the same machine, but I keep getting an error when I hit "Forward" at the partitioning editor...Someone also told me I don't have enough free space.

[http://s185.photobucket.com/albums/x290/Asian_Wannabe/?action=view&current=untitled.jpg](http://s185.photobucket.com/albums/x290/Asian_Wannabe/?action=view&current=untitled.jpg)

Is that enough? I defragmented it too :)

---

### Post by dfreer on 2007-06-02
The problem is Ubuntu is installed to a seperate partition from your windows partition. So if you have 207 GB's free, but it is all in the windows partition, you can't use it, windows is using it :(

Fortunately, this is a pretty straightforward fix. Shrink the windows partition (you already defragmented it so that's good), and then install ubuntu to a new partition in the free space left. I would recommend at least 5 GB's to ubuntu, and 1.5 x the amount of RAM for the swap partition (if you don't know what a swap partition is, just ask and we can explain it, or just use google :D)

---

### Post by dfreer on 2007-06-02
After reading your previous thread, it *could* be a bad CD burn if it won't let you resize your partition. When you start up the Live CD, have it run the CD check, see if the CD is any good.

Another tip is not to post new threads about the same problem, makes it hard on people trying to help you :D it's ok though you're new here, I did it myself when I felt like I wasn't getting enough response when I first started.

---

### Post by Asian_Wannabe on 2007-06-02
How do I shrink Windows O.o?

---

### Post by Asian_Wannabe on 2007-06-02
I just ran an error check on it, ubuntu says the disc is good :D

---

### Post by dfreer on 2007-06-02
you should be able to shrink windows partitions using the install CD, when it comes to the partitioning stage there should be an option, you may need to select "Custom" and partition it from there.

If you can, backup data first.

I'm going to pop a live cd in, to try it out. If you can't figure it out post and I'll  give you a step-by-step.

EDIT: Ok, here we go, with screenshots!
First, select your timezone, language, and keyboard options till you get to this screen, from here select the "Manual" option:
[http://www.dfreer.org/~dfreer/screenshots/install1.png](http://www.dfreer.org/~dfreer/screenshots/install1.png)
You will then be brought to the partitioner screen, which sadly doesn't graphically display the partition info like parted did :( but i digress:
[http://www.dfreer.org/~dfreer/screenshots/install2.png](http://www.dfreer.org/~dfreer/screenshots/install2.png)
You need to select the partition you want to resize, and then click the "Edit Partition" button. Note that I will *not* be resizing mine, I do not want or need to!:
[http://www.dfreer.org/~dfreer/screenshots/install3.png](http://www.dfreer.org/~dfreer/screenshots/install3.png)
Make sure to specify the new partition size to be LARGER than the amount of Used Space. In my example, I am resizing it from 20974 MB's to 15000 MB's. Make sure you know how much space you want to give ubuntu, plus 1.5 x amount of RAM.
From there, it will bring up a confirm box. Pay attention, the changes you make here CANNOT be undone. 


Now, Let's assume I did the resizing. The screen should looks similiar to mine now:
[http://www.dfreer.org/~dfreer/screenshots/install4.png](http://www.dfreer.org/~dfreer/screenshots/install4.png)
Now, from the free space you have available, create a new partition. Make it 1.5 x amount of RAM, so for my system that has 1 GB of RAM I will make it 1500 MB's. Select swap for the filesystem type then hit ok.
[http://www.dfreer.org/~dfreer/screenshots/install5.png](http://www.dfreer.org/~dfreer/screenshots/install5.png)
Again, by clicking on the free space, and then hitting the "New Partition" button, create another partition for ubuntu to fill the available space left. I would recommend reiserfs filesystem, but ext3 and XFS are also popular. Make sure to change the mount point to /
[http://www.dfreer.org/~dfreer/screenshots/install6.png](http://www.dfreer.org/~dfreer/screenshots/install6.png)

Click forward and proceed with the rest of the install. Good Luck!

---

### Post by Asian_Wannabe on 2007-06-02
I've been trying to get this thing working for a couple weeks now ^_^; a guide would be very useful, also I don't see a shrink windows option, there's a resize and use freed space option if thats what you meant. Thanks!

---

### Post by dfreer on 2007-06-02
see above, i didn't make a new post for the how to :D

---

### Post by Asian_Wannabe on 2007-06-02
At your third step (Install3), I typed in a new size and hit Ok, then I got the "Are you sure you want to do this? Can't be undone" thing and hit Ok there too...but then I got this message.

Resize Operation Failure

An error occured while writing the changes to the storing devices.
The resize operation is aborted.

=/ sorry for being so much trouble

---

### Post by dfreer on 2007-06-02
It's more than ok, I'm sorry the installer is giving you such a hard time. Is this just a plain NTFS partition, are you using vista/encryption/anything else that might make resizing NTFS a pain?
Also, how much did you resize? You want to specify a size that is larger than the amount of space windows is using, with a margin of error. So if you are using 16.8 Gb's, let's give it at least 20 Gb's of space. You will need to specify it in ubuntu with a value >= 20000, kay?

If nothing else, try finding something that can resize NTFS paritions, for example Partition Magic (partition magic doesn't ALWAYS work, it's basically like playing russian roulette!). 

The best option is to move your data somwhere else, completely repartition the drive with your favorite partitioner (the Live CD works great, just use it to delete/create partitions, then use windows to format and install, and then go back to the live cd and install ubuntu), and then put your data back on the drive.

---

### Post by Asian_Wannabe on 2007-06-02
I'm putting a larger number than my used...also I just realized, this computer has pretty much nothing installed on it, so I'm just gonna uninstall it and partition that way :) thanks for all the help...oh...may be a bit off topic but I haven't been able to connect to the internet on the Live CD. I use a Compact Wireless-G USB Network Adaptor with Speedbooster (model WUSB54GSC)...ubuntu doesn't seem to detect it :( is there anything I should install before I remove windows that will detect my wireless thing?

---

### Post by dfreer on 2007-06-02
Good, at least your willing to do that, most users freak out when they hear anything about reinstalling windows. Ubuntu doesn't need that much space, itself. Like in my system, I give the root partitions (I run AMD64 and 32-bit Ubuntu) both 6 Gb's apiece, and then share a /home partition of 40 GB's to hold my music and settings. I have installed ALOT of programs, and I use about 2-3 GB's on each / partition. However, you have PLENTY of hard drive space, feel free to give ubuntu more so that you don't need to worry about running out. 
Also note, you may want to make a shared fat32 partition of several Gb's, so that you can easily share files between windows and ubuntu. You can even make this huge, so that all of your music, documents, etc are in one place and both OS's can see them. Ubuntu can read (and with a driver, write) to NTFS, but not the other way around.

just make sure to install windows before ubuntu so you don't have to mess with windows overwriting your MBR and having to reinstall GRUB.

Internet is going to be a problem. From what I've seen, almost everyone has problems using those wireless USB dongles in ubuntu. Try doing a google search for a how-to, but I doubt it is going to work. You could simply buy a $10 Wireless PCI card that would work in Linux...

---

### Post by Asian_Wannabe on 2007-06-02
Any specific wireless cards you would recommend?
**also I plan on playing WoW on ubuntu (if I could manage to get it working I may just uninstall xp for good) so I may need a fairly good connection**

---

### Post by dfreer on 2007-06-02
Intel cards I haven't ever had problems with, only they do not generally use open-source drivers the drivers are easily installed with the Restricted Driver Manager (on my laptop with an Intel PRO 3945 A/B/G wireless card, the live CD automatically installs the driver when it loads anyways, because it is considered essential I believe).
Other than that, I haven't used too many wireless cards. I know everyone says Atheros Chipsets rock, but I don't know which cards use that chipset. A google would be your best bet, or a search on this forum. Also if you don't find any create a new thread for it, someone surely knows around here :D

Ok, WoW should be pretty easy to install with Wine. The most important part is getting your video driver working correctly. ATI drivers are a *pain* to work with, although it can be done it will take some wrangling. Nvidia should be as easy as using the restricted drivers manager. If you can't get WoW working, do a search for a guide, and if you still have problems create a thread and pm me with a link so I can check the thread out.


STAY CLEAR OF BROADCOM CHIPSETS!!! important enough to shout out, broadcom cards are notorious for not working. just don't do it. The default Dell laptop uses broadcom chipsets, although i don't remember the name of the card itself that uses it. Just make sure to check it isn't broadcom!

---

