---
title: "How to show separate partition in files"
date: 2022-08-18
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-08-18
I have a single 1tb ssd as my main drive.  The ssd has two partitions.  The first is 537mb and is, I think, for booting.  The second partition is 967gb.  What I would like to do is to get the second partition to display itself in files.  I have given it the name of data4.  It mounted at the "Filesystem Root".  Right now I have to press "other locations" to get to it (its listed as 'computer')  

and then I REALLY screwed up.  I told discs where to mount the second partition and that was a huge mistake as I was changing where everything but boot was and so it lost its way.  Is here anyway I can get into grub and fix what i screwed up?  

If not then I am trying to get to the bios so that the machine will boot off the 22.04 install stick and just re-install everything and have at it again (this time, hopefully, no more screwing up)  'Del' usually does that but not with this machine.  I know how to get to grub but that's pretty much it.  I tried pressing the del key, f11 and f12 as well but nothing seems to want me to get to the bios so I can tell it to boot off the stick.  If I can get to the install stick I might even be able to fix my screwup (not sure) from the stick.  

Thank you...............

---

### Post by ubfan1 on 2022-08-18
Use Google to search for the key to invoke the UEFI settings, try ESC, F1 and F2.

---

### Post by vanadium on 2022-08-19
You do not want nor need to have an icon to quickly access the root directory of your system partition. Access to that partition is only needed when doing system administration, and then, it is easy enough to navigate there using "Other Locations".

> 
Is here anyway I can get into grub and fix what i screwed up? 

This will not help. Since no system partition is defined anymore, the system cannot boot. Not normally and not in recovery mode.

Instead boot a live session from a live DVD or USB. This will allow you to access the fstab configuration file on the partition that should function as your system partition, and edit it to undo the harm. When, in Disks, you play with the mount options, it is the configuration file `/etc/fstab` that is being changed when "Mount at system startup" is checked. Beware: it is "/etc/fstab" from within your running system, but from within a live session it will be "/<wherever your system partition is mounted>/etc/fstab".

---

### Post by yancek on 2022-08-19
>  The first is 537mb and is, I think, for booting.  The second partition is 967gb.    

That looks like a standard install with the 537MB partition being the EFI partiton and the 967GB being the Ubuntu filesystem.  The method you describe in your first paragraph is the standard in Ubuntu.  In Files (nautilus) you should have a listing of directories in the left panel including Home, Downloads, etc.  This allows you to access those directories directly without navigating to them.  Filles will usually open in the /home/user directory of the user logged in.  That user should have full access to those directories but generally not to other system files outside /home/user.

You can't 'fix' this with Grub.  Did you happen to make a backup of the /etc/fstab file?  If so, you might be able to repair it by unmounting   You could try, if you can still boot Ubuntu unmounting the data4 and remounting it back to where it was, at root ( / ).  I doubt you can boot after doing this.  You might be able to do it with the Ubuntu install USB but it would be a convoluted process.

If you wanted a separate partition for data, you could have used GParted or another partition manager to shrink the largest partition and creating another data partition.  Many  users create a separate /home partition during the install which you could do if you reinstall.  The method of having Other Locations to access the filesystem is deliberate as there is no reason for a standard user to access those locations unless doing system changes as explained above.

The key to use to access the BIOS firmware to change the boot device order varies with manufacturers and the same manufacturer will have different key for differnt model of the computer so you need to either post here which company manufactured the computer (HP, DELL, Lenovo, etc.) and do an online search for the manual to get the correct key..

---

### Post by jgw on 2022-08-19
Thank you for all the replies!

I have been giving all of this some thought.  I think the easiest way to go is to simply do a new ubuntu 20.04 install.  Its easy, pretty quick and then I can have at it.  My need for the access to the large drive is really not necessary.  If I need to see more than the home directory I can just go to 'computer'.  My thought was just wrong and made no sense.  I seem to have got stuck on it and never thought it through - sign of old age I fear.

Thanks again!

---

