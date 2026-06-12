---
title: "Disk partitioning fails during Xubuntu 7.04 installation"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by rwnz on 2007-04-21
I've attempted to install Xubuntu 7.04 onto my Toshiba Satellite 1800 PIII 850MHz laptop with 256MB RAM & 15GB HD. It was loaded with and successfully running Xubuntu 6.10. As I'm doing this to experience Linux there were no important files on it so I tried to install the new OS over the old by selecting the option of rewriting the partitions. I'll describe my process:
1. Boot off xubuntu-7.04-desktop-i386.iso cd
2. Xubuntu 7.04 loaded to the login screen requiring username and password but I could not find a combination that worked!
3. Rebooted off xubuntu-7.04-desktop-i386.iso cd
4. This time it booted fully to the Xubuntu desktop (In playing around I found this double boot process was initially required each time I try to install Xubuntu 7.04 to get around the login issue, but in later attempts it has been going straight to the desktop!!)
5. Ran the Install file on the desktop to change from the live CD to a permanent installation
6. When entering the partitioning parameters I selected to automatically use the entire disk for the new partitions
7. Had the following error message returned during the partitioning process:
        Failed to create a file system
        The ext3 file system creation in partition #1 of IDE1 master (hda) failed
8. I tried manually creating partitions with (I may be wrong here but I know little about this side of things):
/dev/hda
       /dev/hda1 ext3 / 14418MB
      /dev/hda5 swap 628MB
9. Received the same error message
10. (I noticed the / had become /media/hda1 automatically)

---

### Post by jerrylamos on 2007-04-21
Just from your writeup the symptoms look like those from the Xubuntu Alternate install I tried.  See [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908)

What did work for me was to "edit" the partition to change the mount point to "/" and select format.  Install went on to format the / partition and the swap file(s), and install completed.  

Now I was testing manual partitioning on the .iso so I didn't look for any other solutions.  For partitioning if you do want to re-arrange things, I have had luck with: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) which is a stand alone partitioner.

Cheers, Jerry

---

### Post by dgraham on 2007-04-21
I had the same problem. It's the magic automounting. I fixed it by editing fstab. See

[http://ubuntuforums.org/showthread.php?t=414276](http://ubuntuforums.org/showthread.php?t=414276)

for a full explanation.

---

### Post by rwnz on 2007-04-21
Thanks. First I followed the link supplied by jerrylamos and it ended at the following which solved my problem:

A workaround for users of Xubuntu 7.04 with existing partitions on their drives is as follows:

  Boot the desktop CD.
  Go to Applications -> Settings -> Settings Manager.
  Select "File Manager".
  Switch to the "Advanced" tab.
  Click on the "Configure" link ("Configure the management of removable drives and media ...").
  Uncheck "Mount removable drives when hot-plugged" and "Mount removable media when inserted".
  Close all the windows just opened, and start the installer.

It is located at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259)

With regard to your suggestion about gparted though I had not mentioned it I had used gparted to erase the partitions as part of my attempts to find a solution myself.

Withe regard to dgraham's suggestion, I didn't try it as I solved my problem first, but it looks like it may achieve the same thing.

---

### Post by Toshibi on 2007-04-22
The fix worked perfectly. I nearly pulled out the hair that turned grey the other morning working on this exact problem! Thanks!:KS

---

### Post by jsmumma on 2007-04-23
> **rwnz said:**
> Thanks. First I followed the link supplied by jerrylamos and it ended at the following which solved my problem:

A workaround for users of Xubuntu 7.04 with existing partitions on their drives is as follows:

  Boot the desktop CD.
  Go to Applications -> Settings -> Settings Manager.
  Select "File Manager".
  Switch to the "Advanced" tab.
  Click on the "Configure" link ("Configure the management of removable drives and media ...").
  Uncheck "Mount removable drives when hot-plugged" and "Mount removable media when inserted".
  Close all the windows just opened, and start the installer.


I have been using Ubuntu for about six months on several systems, but I'm new to Xubuntu. I ran into this same problem when trying to install Xubuntu 7.04 on an old AMD K6-2/300MHz system that formerly was a dual-boot setup between Dapper Drake (nearly all the time) and Windows XP SP2 (only rarely). I figured that Xubuntu would be a good fit for this system.

The problems I have in using the information provided in these forum posts are admittedly due to my lack of experience with vi and Xubuntu. I can learn enough vi to edit /etc/fstab as described, but I'm confused about the steps outlined in the quote above. I downloaded xubuntu-7.04-desktop-i386.iso and burned it to a CD-R. I placed it in the CD-R/W drive in the target system and booted the system. When the Xubuntu screen appears, I select the first option, which includes the Install option. Eventually the desktop appears with several icons.: Floppy Drive, Trash, Home, Filesystem, Examples, Install. (I also get "/" and "8G Volume" or "4G Volume", but these appear based upon previous install/partitioning attempts and the fact that there are two internal drives: /dev/hda is a WD 8.4 GB drive and /dev/hdb is a WD 4.3 GB drive.)  I don't see anything but these few icons on the screen. How do I get to a menu that shows "Applications" so that I can navigate Applications -> Settings -> Settings Manager?

---

### Post by zazen666 on 2007-04-23
> **jsmumma said:**
> I have been using Ubuntu for about six months on several systems, but I'm new to Xubuntu. I ran into this same problem when trying to install Xubuntu 7.04 on an old AMD K6-2/300MHz system that formerly was a dual-boot setup between Dapper Drake (nearly all the time) and Windows XP SP2 (only rarely). I figured that Xubuntu would be a good fit for this system.

The problems I have in using the information provided in these forum posts are admittedly due to my lack of experience with vi and Xubuntu. I can learn enough vi to edit /etc/fstab as described, but I'm confused about the steps outlined in the quote above. I downloaded xubuntu-7.04-desktop-i386.iso and burned it to a CD-R. I placed it in the CD-R/W drive in the target system and booted the system. When the Xubuntu screen appears, I select the first option, which includes the Install option. Eventually the desktop appears with several icons.: Floppy Drive, Trash, Home, Filesystem, Examples, Install. (I also get "/" and "8G Volume" or "4G Volume", but these appear based upon previous install/partitioning attempts and the fact that there are two internal drives: /dev/hda is a WD 8.4 GB drive and /dev/hdb is a WD 4.3 GB drive.)  I don't see anything but these few icons on the screen. How do I get to a menu that shows "Applications" so that I can navigate Applications -> Settings -> Settings Manager?

All the icons and such you mention seem normal for your system."Applications" should be on the toolbar at the top next to the firefox icon.
I had the same problems as some have mentioned above using xubuntu to reformat my HD partions. I used GPartion, which is a live disc that will allow you to partion your HD. I made a linux swap of 1.5 gigs, and used the rest as "/" which means root. Then I put in the Xubuntu live disc again. The intall worked fine then.

---

### Post by jsmumma on 2007-04-23
Thanks for the quick response. I used Acronis Disk Director Suite 10.0 running from a "Rescue" CD to repartition the drives, since I already had it. This, of course, had no effect since the problem was not the disk partitioning itself (which I did not know until I read these forum threads). I will, however, look into Gparted for future use.

I guess I did not make myself clear regarding my problem with navigating Applications -> Settings -> Settings Manager on this system. When I said "I don't see anything but these few icons on the screen", that is exactly what I meant, i.e., ***there is no toolbar!*** ](*,) Any clue(s) as to why this might be the case?

---

### Post by zazen666 on 2007-04-24
I guess I did not make myself clear regarding my problem with navigating Applications -> Settings -> Settings Manager on this system. When I said "I don't see anything but these few icons on the screen", that is exactly what I meant, i.e., ***there is no toolbar!*** ](*,) Any clue(s) as to why this might be the case?[/QUOTE]

Im sorry but i would not know what there is not toolbar. Maybe an error with the live CD?
You can try this though.
Right click the desktop=>desktop preferences=> go to the "behavior tab"=> under MENU check "show desktop menu on right clikc"

That will give you all the same menu as the toolbar.

Good luck

---

### Post by jsmumma on 2007-04-25
zazen666: That did it! After making the setting changes described by rwnz above, I was able to complete the installation. I am now looking at my Xubuntu 7.04 desktop with Menu bar at the top (Applications, Firefox, and Home folder on the left; date/time and Quit on the right), Panel at the bottom (with four workspaces and trashcan on the right), and desktop icons for File System, Home, Trash, Floppy Drive, and another icon for a second hard drive (hdb). I never would have gotten past this problem without help from the forum. Thanks again! Meanwhile, the upgrade of an older notebook (HP Pavilion N5425) from 6.10 to 7.04 is in progress. My workhorse HP Pavilion ZV6100 will be the last to upgrade to 7.04.

---

