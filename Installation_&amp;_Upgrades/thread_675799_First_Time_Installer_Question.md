---
title: "First Time Installer Question"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by TakashiStormii on 2008-01-23
i am about to install ubuntu for the first time. i currently have windows xp. will i have to do a clean install. meaning, will i lose everything on my drives? is it worth it? i just dont care for windows anymore...and im no millionaire, so i cant get mac.

---

### Post by yota on 2008-01-23
Even if there's a small risk of data loss in an installation process (=backup anything important to you) you are not supposed to lose anything if the process works fine.

See documentation at: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

and particularly at: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) as you can see in the pictures the ubuntu installer will take care of resizing the windows partition and install in the free space (if you tell it so). It's better if you do a defrag from windows before starting the ubuntu installation.

Hope this helps!

---

### Post by vipin on 2008-01-23
Its simple, just follow these steps:---

Lets say you have two partitions in Windows XP.

Say C drive where your Windows XP is installed and a D drive where you keep your songs installed etc.

Assuming that your D drive doesn't have that much important data, i take like you can delete.

Go to My Computer -> Right Click -> Choose Manage and then on the left hand side choose "Disk Management"

Now it will display your harddisk partitions, delete D Drive.

Now restart your computer and insert Ubuntu CD, setup will start, and you can have Manual Partitioning.

Even I am a new user for installation, you can just set the partitions of the FREE SPACE, make two partitions, one for 1.5 X RAM size for SWAP type partition and choose the rest partition as ext3 with mount point "/" and let the setup continue.

hoping this helps to you.

vipin

---

### Post by housam on 2008-01-23
For a beginner , don't delete windows till you get used to ubuntu. and back-up your data anyway.

---

### Post by TakashiStormii on 2008-01-23
how do i install without getting rid of windows? and how do i get rid of windows further down the road? is ubuntu really faster and better than windows xp?

---

### Post by housam on 2008-01-23
Yes ubuntu is better and faster than win-xp.
You can make a dual boot installation . 
--------------------------------------------------------------------------------

- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.
- You can create up to only 4 primary partitions on single HDD.
-I suggest to create 3 primary partitions and make the 4th one as extended which can be devided to many logical partitions.
- You'll devide the extended partition to 2 partitions : one EXT3 ( 20 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

GOOD LUCK
__________________

---

### Post by rosegarden78 on 2008-01-23
Basically:

On Step 4 of your Ubuntu Installation - manual or custom split your disk into 2 Primary partitions instead of one as usual.  Do not use extended partition is no good.  Only Primary partitions are OK!

Then Ubuntu should automatically handle the new partition for you.

---

### Post by mikeparent on 2008-01-23
I too just installed ubuntu over wondows xp.  i love it.  however (and maybe someone here can help me), i want to install skype and flash player.  once the download is complete to my desktop, i can't install.  why not?  is there an easy way to install 3rd party linux supported programs?

---

### Post by Kevbert on 2008-01-23
> **mikeparent said:**
> I too just installed ubuntu over wondows xp.  i love it.  however (and maybe someone here can help me), i want to install skype and flash player.  once the download is complete to my desktop, i can't install.  why not?  is there an easy way to install 3rd party linux supported programs?
Installing 3rd party software is easy.  First you need to check how your software sources are set up.  From the task bar select System - Administration - Software sources.  Enter your password when prompted.  Under the Ubuntu Software tab check all boxes are ticked.  Under updates check at least Important security updates and Recommended updates are checked.  Then close the window.  Now from the task bar select Applications - Add/Remove.  In the box marked Show select All Available Applications.
Regarding flash player you may not be able to run this in a browser as there is currently a problem with the download.  I don't know about Skype.
One thing you may want to try is Automatix from which you can download virtually all codecs you'll ever need [http://www.getautomatix.com]("http://www.getautomatix.com").  It works in a similar way to the Add/Remove.  I recommend you get the Xine version of the Totem media player via Automatix.

---

### Post by TakashiStormii on 2008-01-23
when i tried to install ubuntu, the picture did not fit my screen at all, i could barely see the "start menu". what gives?

---

### Post by rosegarden78 on 2008-01-26
Wowsers!  What screen did the disc boot?  Did you choose first option?  Did the LiveCD load to a desktop?  Did you click Install and did that screen freeze?  Ubuntu doesn't have start button per se.  That's a windows thing but you can customize it.

---

