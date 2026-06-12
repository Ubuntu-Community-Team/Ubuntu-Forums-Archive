---
title: "How to partition, and other problems"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by Comrade on 2005-07-20
Hello, everone. I'm trying to get Ubuntu to install, but I do not want to annihalate my existing Windows partitions. Here's my partition table.

IDE master (hda) - 120.0 GB
#1 primary 6.9GB fat32
#2 primary 85.2GB (lightning bolt arrow) ntfs
#3 primary 108.4MB  :) ext3
#5 logical 27.8GB :) lvm

The first partition is the XP CD partition. The second is my Windows XP Home partition. The third is my FC3 partition which I want to destroy/overwrite, and the fifth...I'm not entirely sure. 

Also, I don't know what the lightning bolt arrow and the smiley faces mean. I assure you, they were in the partition table. 

Another question: how do I prevent Windows from destroying the MBR after I write grub to it? 

It would be very nice if someone could outline the steps I need to take in order to install Ubuntu, without risking the deletion of the Windows partitions. I would rather not even access or modify the Windows partitions during the installation. Is there an option, like in the Fedora Core installer, which allows the installer to ignore and avoid all non-Linux partitions? If not, how would I install Linux?

If you need more information from me before you can help solve my problems, please ask. I don't want a wrong answer because I didn't provide enough information.

Thanks for the help?

---

### Post by jesse on 2005-07-20
You need a Knoppix live linux cd, which contains the ntfs partition resizer qtparted. 

Download Knoppix at [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html) 
(You will turn the iso into a bootable cd)

Before you boot with the Knoppix CD, run defrag.exe under Windows XP. Let the defrag program finish and don't use your computer or run programs until it does or it will keep restarting and never get done. You may need to disable your Windows screensavers or other running nonsense first. 

After, and truly only after, you have defragged Windows, put the Knoppix CD in and reboot. 

You will boot into a version of Linux called Knoppix that runs entirely on cd. Once in it (You'll be in the kde desktop) you can use the program Qtparted to resize your ntfs partition and create a linux partition (e.g. ext3) onto which you can install ubuntu. 

Your ext3 partition should be at least 4G I think, since I read somewhere the Ubuntu installation process needs at least that much. 

When you run the Ubuntu installation CD, you'll be asked what partition you want to put it on. Select the ext3 one you've created. This will not touch your XP (if you really think you still need it :grin: 

Your ubuntu installation should create a grub entry for Windows XP, too. 

**I PROVIDE THIS WITH NO GUARANTEE, BUT IT'S WORKED FOR ME. BACKING UP IMPORTANT DOCUMENTS ETC ON WINDOWS BY BURNING THEM TO A CD OR DVD IS RECOMMENDED JUST IN CASE SOMETHING GOES WRONG. ** 

The Knoppix CD will also be useful if your Windows ever becomes unbootable. 

My mother had a problem with her Dell desktop pc that Knoppix saved. She had tens of gigabytes of photos and other files on her Windows XP when all of the sudden Windows unexplainably became unbootable. The Dell customer service people told her all her data was gone and the only thing she could do was reformat her hard drive (erasing everything) and reinstall XP. 

However, Dell was wrong. Upon booting from the Knoppix CD, her entire Windows partition was accessible simply by clicking on an icon. We then proceeded to successfully burn everything to CDs and DVDs, using the linux cd burning program k3b under Knoppix.

---

### Post by jesse on 2005-07-20
**OR BETTER YET!** 

My guess is that the ext3 you already have that's about 100 MB (way way too small for an entire operating system) doesn't have your entire Fedora, but only the /boot folder and that the LVM is the rest of your Fedora. Keep in mind though, this is only my guess. 

You may be able to avoid having to resize your Windows partition at all by simply using Knoppix to turn the LVM into an ext3 and deleting the smaller ext3 using qtparted. 

**BEFORE YOU DO THIS THOUGH** 

boot into the Knoppix CD and look at the KDE desktop icons. You should have an icon for every automounted hard drive partition, including the LVM. Try clicking on the LVM to see what it contains. If you see your Fedora files and directories on it, you can get rid of it as described above and put Ubuntu on it rather than resizing your ntfs.

---

### Post by Comrade on 2005-07-20
And how would I do this?

---

### Post by jesse on 2005-07-20
Download the Knoppix iso from the website I posted and burn it to a cd using Windows. Or you can order one either from the site or from Ebay. 

Then pop the Knoppix cd in your computer and restart. You will end up in KDE, which looks a lot like Windows but is a Linux desktop environment. 

You will then see icons on the desktop for your existing hard drive partitions. Click on each of them and view their contents. If you see your Fedora files in one, note the size of the partition. (Right-click on the icon and select properties). Remember the size and other information displayed. 

Then log out of kde and choose "shutdown" (much like in Windows) Knoppix will shut down and automatically eject the cd. Turn your computer back on and boot with the Ubuntu installation CD. When the installation program loads the partitioner, select the one that had Fedora on it as the one you want to put Ubuntu on. You should recognize it by its size now. 

Don't touch the one that says ntfs and your Windows XP will not be touched or affected.

---

### Post by Comrade on 2005-07-21
And how do I select the Fedora partition as the one I want Ubuntu on?

Also, what do I do with the other partition? I think that the one with 27.8GB is the Fedora partition, but I'm not sure. I don't want to waste so much valuable space.

---

### Post by jesse on 2005-07-22
When you boot the knoppix live linux cd as soon as the desktop appears you will see hard disk icons on it that literally look like hard disks. Click on each of them and they will open in konqueror, a program a lot like Windows explorer which will show their contents and files. You can right-click on each disk icon on the desktop and select properties to determine its size. If you can tell by the contents as displayed in konqueror which one is your Fedora partition and that partition's size is the 27G when you right-click on it and select "properties" then you will know when you install Ubuntu that you need to select the partition that is 27G as the one you want to put Ubuntu on. 

It may seem complicated now, but once you run the Ubuntu installation program it will suddenly appear very simple.

---

