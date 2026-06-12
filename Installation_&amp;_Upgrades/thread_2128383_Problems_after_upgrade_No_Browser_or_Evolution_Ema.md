---
title: "Problems after upgrade: No Browser or Evolution Email"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2013-03-23
Well my trepidation on going from 10.04 to 12.04 has been transformed into a serious OH ****!
Here's what happened:
Downloaded 12.04 off torrent sites, verified checksum values, burned a CD, booted off CD for the 12.04 install.
It soon asked if I wanted to  1.do a clean install and overwrite 10.04
                                         2. remove Windows XP and Linux 10.04 and install 12.04
                                         3. delete entire partition(s) and start from scratch
                                         4. Custom install
I selected number one [Wrong!!!] and then realized when it never asked me for partitioning information on root and home during the install that I was in deep trouble. The install itself went fine as I am under 12.04 typing this. But everything is lost from 10.04 as far as the desktop is concerned. I can go to /home and see my user folder (and my wife's). The folders still have all our personal files intact. I have a current 10.04 backup on a different drive that I thought I could use "to clear the air" but when I invoke the 12.04 Backup utility and do a search it says there is no backup. ???

What is the easiest solution to my present situation? Reinstall 10.04 and do a backup and then reinstall 12.04? I hope not. There should be a straightforward way to copy some files from here to there or something to get things bck in order. Everyone said a clean install was the way to go but selecting option 1 instead of option 4 was a big mistake, in my particular case. 

Any help from the younger geeks and gurus would be very appreciated.

Ed

---

### Post by dino99 on 2013-03-23
Something i cant understand:
- you says : 12.04 installed & working smootly. So why would you redo that install stuff ?
- you also says: my data is safe  as well my wife's . So everything is as good as possible dont you ?

So what your backup have you are missing ?

If you had googling a bit about the installer (ubiquity) before going into trouble, you will have found so many complaints about that confusing/buggy app & also how to do a manual install (always better to trust yourself).

---

### Post by ozark_hillbilly on 2013-03-23
OK folks. What do I do to get things linked/cleaned up? My Desktop is empty, etc. I had a separate /home partition which appears to not have been muddled with during the 12.04 install. Will I still have a Desktop screen like when using 10.04? Do I need to download Goggle Chrome and will my old browser configuration pick back up? My Evolution email data -where is that now at?

---

### Post by ozark_hillbilly on 2013-03-23
bump

---

### Post by Bashing-om on 2013-03-23
ozark_hillbilly; Hi !

Standard install of 12.04 gives "unity" as the desk top, in the launcher (left side of screen) is a folder icon that activates the file manager "nautilus"; in nautilus on the left side pane are listed all the file systems that ubuntu is aware of. Can you not copy with nautilus -from one window to another- any files you need to copy across to the new install ?


[INDENT=2]just my thought 

 	
[/INDENT]

---

### Post by ozark_hillbilly on 2013-03-23
Yes. I did go ahead and copy from my user/desktop folder to the Unity Desktop and that seemed straightforward enough. Unity is a little confusing at first. My biggest question is this:
If I need to reload/install all my old apps will this process overwrite any existing areas that have my current data files under /Home/User. For instance if I download/install Evolution and Google Chrome will this effect my address book and bookmarks respectively? Or will all that automatically link back up and use the pertinent files in my User folders?

Thanks,

Ed



> **Bashing-om said:**
> ozark_hillbilly; Hi !

Standard install of 12.04 gives "unity" as the desk top, in the launcher (left side of screen) is a folder icon that activates the file manager "nautilus"; in nautilus on the left side pane are listed all the file systems that ubuntu is aware of. Can you not copy with nautilus -from one window to another- any files you need to copy across to the new install ?


[INDENT=2]just my thought 

 	
[/INDENT]

---

### Post by Bashing-om on 2013-03-23
ozark_hillbilly;;

uhhh, Anytime a config file is over written then whatever was the old config file is gone and the new config file is in effect. That said, can not hurt to look at each and make any wanted edits.
Chrome I have limited experience with. In firefox there is a procedure to export all ones preferences, bookmarks and such to a external medium, and import them back to the new install. I bet the same is doable in Chrome.

Unity observation: I installed 12.04 about a year ago (triple booting) and kept 10.04. After a bit of getting accustomed to the new interface and learning my way around, I find I prefer Unity and have not gone back to 10.04. Nor, have I replaced the unity desk top. Unity is different and takes a new outlook to find/accomplish tasks, but, once you know how - unity is faster and easier ! I did find that indepth documentation is lacking.


[INDENT=2]it's all a learning experience

 	
[/INDENT]

---

### Post by oldfred on 2013-03-23
If you did an auto install, it would create a new /home and not use a separate /home if that is what you have.

But you should be able to edit fstab to add your old /home into your new install. It would be like create a new separate /home without the first few steps of creating a partition and copying data to it.

If you have the separate /home then it should just be the last steps on editing fstab. You may get some ownership issues if you have multiple users and did not create in same order.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by ozark_hillbilly on 2013-03-23
@ Oldfred

Looked at the link you provided but this is all getting out of my league at this point. I am not sure where to put what and in what ordrer.  Can I do a reinstall of 12.04 and select number 4 for a custom install or has the partition stuff been irrevocably altered at this point. I noticed that the 12.04 install is using A LOT MORE of my drive space now than 10.04 was. I am going to keep inadvertently screwing up and lose my personal data at which point I will probably just chunk this computer off the bluff I live on top of. Too much frustration right now.....

Ed

---

### Post by oldfred on 2013-03-23
Reinstall may be quicker. You do have to use manual partition, choose each partition, select format, and mount. But with an existing /home you choose it but DO NOT FORMAT it. Uncheck anything that may reformat your existing /home.

If you want we can give info on editing fstab.

Post these.
       sudo blkid -o list
      
  sudo cat /etc/fstab

It will be just the commands from the move home link starting here with your UUID and fstab.

 **Preparing fstab for the switch**

---

### Post by ozark_hillbilly on 2013-03-23
@ Oldfred

admin@ed-Desktop:~$ sudo blkid -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs             (not mounted)  30182B1D182AE218
/dev/sda5  ext3    HOME     /media/HOME    3d34262b-e98a-441c-bc7a-e3a3989d1378
/dev/sda6  swap             <swap>         2a8810b8-d6e6-4c2b-a89c-fb345ca0a122
/dev/sda7  ext4             /              ba167dfa-471a-4ee5-940e-7c67e3931ce3
/dev/sdb1  ext3    Backupdrive /media/Backupdrive 7a117704-c5b0-4858-92c4-16e95deb55f9
/dev/sdb5  ext3    Drive 2: sdb5 (not mounted) 07cbf7e3-e34c-429a-b26a-00dbe44a9884
/dev/sdc1  ntfs             /media/4CB9BA847381C91A 4CB9BA847381C91A


*****************************************************************

admin@ed-Desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ba167dfa-471a-4ee5-940e-7c67e3931ce3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2a8810b8-d6e6-4c2b-a89c-fb345ca0a122 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
admin@ed-Desktop:~$

---

### Post by ozark_hillbilly on 2013-03-23
@ Oldfred

Is the line with the > < what  I need to insert? Do I need to save or backup anything first?

**********************************************************

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0

> UUID=3d34262b-e98a-441c-bc7a-e3a3989d1378 /home ext3 errors=remount-ro 0 1 <

# / was on /dev/sda7 during installation
UUID=ba167dfa-471a-4ee5-940e-7c67e3931ce3 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=2a8810b8-d6e6-4c2b-a89c-fb345ca0a122 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

---

### Post by oldfred on 2013-03-23
I might change a couple of settings. Just use defaults and 0 2 not 0 1.

       UUID=3d34262b-e98a-441c-bc7a-e3a3989d1378 /home ext3 defaults,errors=remount-ro     0       2
         
      
 sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a

You still will have your old (was new) home folder in / (root). If you made any user settings inside your new install, you may want to copy them into your /home. You eventually want to houseclean out the /home/{yourname} folder.

---

### Post by ozark_hillbilly on 2013-03-23
@ oldfred

Modifying Fstab was the solution I believe! Can I now download & install Google & Evolution and it should pick up my user data from the /home folder (ie existing Bookmarks, address book)?

I really appreciate your assistance Fred. Thanks a lot.....

Ed

---

### Post by oldfred on 2013-03-23
Generally applications settings are in /home, so just reinstalling an application will find the previous settings. Most will upgrade ok.

---

