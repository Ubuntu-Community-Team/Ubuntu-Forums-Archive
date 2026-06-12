---
title: "Cannot partition in Gparted!"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by youngunix on 2012-09-10
Hello all, 

I am trying to install Ubuntu 12.04_64bit along side Fedora 17, however, I cannot partition the hard drive from Fedora or Live Ubuntu using gparted (screenshots below). i have looked everywhere on the web for this issue, and I have yet to find a solution.

---

### Post by UltimateCat on 2012-09-10
To look at your current partition.....

You should be able to open the terminal and run:
```
fdisk

```[http://linux.about.com/od/commands/l/blcmdl8_fdisk.htm](http://linux.about.com/od/commands/l/blcmdl8_fdisk.htm)
 
Also; during the installation process you should be able to see all partitions before you create the new partition dedicated for your new distro install '/'

I (think) it's shortly after setting up the clock than the next thing to do during the installation process is the" partition disk".  Every installer is a little bit different tho-

I use the manual option and than expert mode to make the partition for the / and then create the partition for the swap.

Hope this helps-

---

### Post by killtroubles on 2012-09-10
are you using that whole 149 GB partition for fedeora ??

---

### Post by darkod on 2012-09-10
By default it seems that the Fedora installer is configuring all of the hdd as LVM (Logical Volume management).

For LVM you specify one or more partitions to be the physical devices used (in your case /dev/sda2) and then you create logical volumes (or LVs) which can be resized easily with the limitation that the maximum space taken by all LVs can't be bigger than the physical partitions in total.

If you have spare space in your LVM, not belonging to a LV, you might be able to install ubuntu on another LV. You will need to use the Alternate Install CD for LVM support, the live cd doesn't have the support.

You could add the lvm2 package in the live session and that will make it able to see the LVM, but I'm not sure Gparted can work with it. It's much better to do it in terminal.

In terminal, after you add the lvm2 package, you can view the physical devices for example:
```
sudo apt-get install lvm2
sudo pvscan # scans for physical devices part of LVM
sudo vgscan # scans for Volume Groups
sudo vgchange -ay # should activate the VGs if not active
sudo lvscan # scans for LVs
```That can show you how much space the LVs currently take, and you can plan your ubuntu installation. However, it will have to be with LVM too.

---

### Post by youngunix on 2012-09-11
Thanks guys for your replies. 
I wanted to install Ubuntu along side Fedora for two reasons: 
1) I wanted to use mid-high end hardware.
2) I thought [COLOR=DarkRed]*_Ubuntu Builder_*[/COLOR] was crashing because of hardware issues. I was very wrong, [COLOR=DarkRed]*_Ubuntu Builder_*[/COLOR] is extremely buggy(simply put: it does not work). 
I'm using Ubuntu_32bit on another machine and very happy with it. 
**This is for anyone that's going to look for a solution to this problem: **
1) Install Ubuntu first, then Fedora.
2) Use the solutions above (if you have already installed Fedora first).

---

### Post by oldfred on 2012-09-11
Some have posted here that when installing Fedora do not use the LVM, just install to a standard Linux formatted partition. That works better for multiple installs unless you do want the entire drive as LVM.

Having just one partition as LVM offer all the disadvantages of LVM without the advantages.

Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

