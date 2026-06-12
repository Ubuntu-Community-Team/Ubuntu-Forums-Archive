---
title: "Adding new hard drive for Karmic"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by timgood on 2009-10-22
I would like to add a new, bigger hard drive and do a fresh install of Karmic on it when it is released. I would like to keep the old hard drive which currently has Jaunty and Windows installed, and after transferring my data and desktop settings to the new installation, would like to resize it for use by Windows. So I would have one big drive dedicated to Karmic, and a smaller one for Windows 7.

So my questions:

1. What is the easiest way to do this?
2. Will I need to remove grub from the smaller drive? If so how?
3. How will I get Karmic to see the Windows 7 installation?

Ideas and advice gratefully received.

---

### Post by jbrown96 on 2009-10-22
I just wrote up a good directions, but decided they weren't any good. Forgive my brevity, I just wasted 20 minutes and don't want to spend that much time re-typing. 
Karmic has switched to Grub2, and at least to me, is a huge nightmare. The config files for it are not clear at all, and it's just difficult to use. So we are going to do this an easier way.

1) Hook up your new hard drive and boot into jaunty.
2) Use gparted to create your new /home. It should be in system-->admin-->parition editor. If not, then install it from a terminal (apps-->accessories-->terminal) ```
sudo apt-get install gparted
``` Open it up. There is a drop-down menu in the top right. Select your new drive. We need to create a partition on it for /home. I don't know your system specs or the HD space, so I can't give any concrete recommendations, but this partition should be the largest. You will only need to reserve about 6GB for / and maybe 2GB for swap (I never use swap and you probably don't need it either). Create a new partition with your desired size. I strongly recommend ext4. Once you are done with that, there should be an icon on your desktop for your new partition (it may be in places). Double click on it to mount. You should get a file browser for it. Open another one that has your home folder. Show hidden files (ctrl+h). Copy everything except .gvfs and .dmrc. In the new partition, create a folder with your username and then paste everything inside. If you get an error, then you will need to fix the permissions with ```
sudo chown -R $USER:$USER /media/disk
``` that disk part may be different. after you type /media/ press tab twice and you should get all the entries. type the one that makes the most sense. Then try to recopy. Once you are certain that everything has copied, then reboot your computer and install Windows 7. It might not be a bad idea to disconnect your new drive just to be certain that you don't overwrite your data. 
Once Windows is installed, you are all set to install karmic. Be sure to reconnect your new drive. At the partitioning step, choose manual. Then on your new drive, your home partition will already be there. You will need to edit it and choose to make it ext4 and the mount point is /home. BE VERY CAREFUL NOT TO FORMAT IT. You will also need to create another partition for /. I would recommend ext4 for this and 6GB should be plenty. the mount point is / You can also create swap, but it's not essential if you have a decent amount of ram (certainly >=2GB, but less would also work). Note that the installer will complain if you don't create any. At the last step, you want to go into the advanced options. It's really up to you where the bootloader is installed. There are practical arguments for putting it on either disk. 
Let's say that drive A is your windows drive and B is your new ubuntu drive. If A is the first boot device in BIOS, then you may not even get a chance to select ubuntu (since the windows bootloader and not grub is selected). Installing grub to this drive will reduced a configuration step to set your BIOS to boot drive B first. On the other hand, it is a good idea to have your bootloader on the primary system. Let's say drive A breaks, then your BIOS doesn't know how to boot either OS. If drive B breaks, then grub sort of loads, but can't even read the entries, so you wouldn't even be able to windows. There's no right answer here; just do what you think is best, but remember if you may need to make changes to your BIOS. Karmic should detect 7 and be able to use it no problems.

post back if you have questions/problems. Just a suggestion in the future. There aren't many people who check this forum. You would be better putting something like this in absolute beginner or general help; you will get answers much quicker. This forum is usually only used for specific 64-bit problems.

---

### Post by timgood on 2009-10-22
Thanks for your time and help.

---

