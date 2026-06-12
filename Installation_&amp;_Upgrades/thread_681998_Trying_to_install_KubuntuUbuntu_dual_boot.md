---
title: "Trying to install Kubuntu/Ubuntu dual boot"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by Name141 on 2008-01-29
Hello, I was trying to install Kubuntu (and Ubuntu, and Xubuntu) , dual boot.  I made free space of around 20 GBs or so , with ext3 / , so then I had ext3, NTFS (for windows) , and then "unusable space" , so I could not figure out a way to make the swap.  So I end up giving it all back to windows and giving up.  

(along with my dell factory partitions of images and stuff)

I also tried the free space option, but that only comes up once I have my external hooked in, and then it wants to use the external.  It doesn't come up auto without it hooked in.

---

### Post by CheShA on 2008-01-29
Any particular reason why you're triple booting the three OSes?  You could just install the kubuntu-desktop and xubuntu-desktop packages then choose which one you wish to log in to from the login screen.

---

### Post by CheShA on 2008-01-29
actually, looking at your question again, it looks like you're struggling with the install of your FIRST linux, leat alone your second and third!! lol 

When partitioning your drives, it sounds as though you have used up all your "primary" partitions (you are only allowed 4).  If you set up 3 "primary" partitions, then the rest as "logical" you should be able to use all  the space.

---

### Post by aysiu on 2008-01-29
Choose to manually edit the partition table instead of doing the automatic resizing. That way you can specify the exact size of each partition and make sure you have partition for swap created.

---

### Post by Zeroangel on 2008-01-29
remember *raises pointer* an 'extended' partition is just a container for some of your real partitions, it doesnt actually contain a filesystem, just other partitions of filesystems. 

If you have already installed windows on one partition then the ubuntu installer should detect it and automatically add it to the boot list once your ubuntu is instealled.

There are two major ways to partition a dual boot setup
~50% windows -- NTFS (mountpoint -- /media/windows)
~45% linux -- EXT3 (mountpoint is '/')
1GB swapfile

the other way is something like this

20GB windows
20GB linux
1GB swap
remainder shared stuff (music, movies, some windows programs) -- FAT32 (mountpoint '/home/yourusername/shared')

---
The way I do it is to boot into the liveCD and lay out my partitions using gparted, then reboot and run the Windows Installer and set up windows, and once thats done, to set up Ubuntu on the partition that I set aside for Ubuntu.

---

### Post by Name141 on 2008-01-29
It is still unclear to me what I need to do then to do this.  I figured I needed to resize my windows partition , then make the / , then a swap ? all manually ?  I can not lose my data on windows.

---

### Post by Name141 on 2008-01-29
Also, I had no problems on my old machine setting up Xubuntu (without any OTHER OSes or partitions.)   But with this instance I need to keep Dell's partitions, AND windows.  Just resizing the NTFS (Windows) to whatever, to store the / and swap ?  Right ?

---

### Post by aysiu on 2008-01-29
> **Name141 said:**
>  I can not lose my data on windows. Theoretically, resizing the partitions shouldn't affect data on the resized partition, but the only way to be 100% sure of that is to **back up your data**. Do not take a chance, however small.

---

### Post by Zeroangel on 2008-01-29
That sounds about right, the '/' is the main filesystem for your linux and swap is equivalent to the windows swapfile, 500MB to 1GB is good for that.

---

### Post by Name141 on 2008-01-29
So again, I have no idea what to do.  As I get "unusable space" before I am able to create the swap.

---

### Post by aysiu on 2008-01-29
> **Name141 said:**
> So again, I have no idea what to do.  As I get "unusable space" before I am able to create the swap.
Mind posting a screenshot?

---

### Post by Name141 on 2008-01-29
er let me load up the live Cd then.

---

### Post by Name141 on 2008-01-29
Actually I don't currently have time to back up everything then resize the partitions, etc.

---

### Post by TWO on 2008-02-27
I currently dual boot Kubuntu and Ubuntu. I personally found that installing kubuntu-desktop in GNOME flooded my menus with KDE applications which I didn't like, so now I set it up to have both. 

However, I wonder if anyone would know why after having installed Kubuntu (after Ubuntu), I now get a "file system check failed" message when Ubuntu is loading up. It then goes on to say "CONTROL -D will terminate this shell and resume system boot."

If I follow those instructions the OS, loads fine but I'd just like to know if there is a way to remedy this.

Many Thanks

TWO

---

