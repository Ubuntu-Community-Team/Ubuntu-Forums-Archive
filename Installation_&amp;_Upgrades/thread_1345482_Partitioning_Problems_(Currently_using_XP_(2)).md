---
title: "Partitioning Problems (Currently using XP (2))"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2009-12-04
I have Seagate SATA 160 GB HDD. I have one Primary system(C:) 40 GB with3 logical extended partitions 40 GB Each (D:,E:,F:) ..I have a SONY DVD writer (H).
 
I wanted to install Ubuntu by freeing up 40 GB...I used EASEUS partition Manager and deleted Drive G: and it became unallocated/free space.
 
I have a Dell VOSTRO 1500 Desktop...Windows XP installation itself is very strange..I had XP reinstalled once after a system crash....I know its weird but the current Disk Map Structure is as follows...To tell you I dont know how this happened
 
C:   -   (NTFS) Total (78MB - It is not typo it is "mega" and not "Giga"Crazy but dont have a clue) ...This drive does not have anything but has hidden files of boot.ini, Autoexec, page file. IO.SYS , MSDOS.sys , NTLDR and NTdetect ( Hate to use Win terminology in Ubuntu...Sorry...but pl help!!)
 
D: - (NTFS) Total 40 GB - I have stored Data, music,video and misc files
 
E: - (NTFS) Total 40 GB-  Usage same as D drive
 
F : Partition Deleted 
 
G: - (NTFS) 38 GB contains Windows Directory
 
* MEDIA DIRECT - 2GB (This is installed by DELL and is NTFS)
 
There is some correlation between C and G Drive,System boots using C but accesses files in G ( Totally ridiculous) ...I have tried moving the hidden files to G: to atleast have everything in 1 place but once I move and restart, sys wont boot and NTLDR error throws up..Using Linux Live CD , I moved these files back to C: and Win Xp loaded normally.
 
1.I would like to use the deleted partition to install Ubuntu..But partition manager gives an error - "No operating System Found - Entire 160 GB is shown as Free Space  and it asks if Ubuntiu should install in the entire drive"
 
2.Also now, the drive letters are not in Sequence C, D and G and * (MEDIA DIRECT)...I tried using EASEUS to assign a drive letter F to G but it doesnt allow to modify system/Boot partition
 
3. i want to merge G (40GB) and C (78MB) partition as one single drive with Win XP booting from that drive 
 
4. i want to use 40 GB for Ubuntu with Dual Boot
 
Right now by itself Win is not giving any problem. Simple solution is to re-format and start from scratch but I want to avoid that ....Any utility which will achieve the above without major destruction??

---

### Post by darkod on 2009-12-04
You said it yourself, the system is setup that way to have the basic boot files in the small C: and then boot G: from there. Unless you are ready to reinstall I don't see how to change that.
The ubuntu installer might not "see" windows just because of this strange setup, hence the No OS present message.
Another thing, if you're not using MEDIA DIRECT for anything useful, I have seen cases where deleting it helps to at least have more reasonable partition layout. Yours is honestly hell. :) Small partition for win boot files and then windows at the back of the drive, if G: is on the back.

Also, instead of selecting the Install option when you boot the ubuntu cd select Try Ubuntu. That will run it from the cd and then open Gparted (System-Administration) and it will show you your drive and partitions. Also their order. It might clear up few things for you. You can even attach screenshot here if you want to, ubuntu will be online and you can do it easy. Gparted might also show you any possibility of merging because you can only merge neighboring partitions. Another option to show disk layout in text version is open terminal (Applications-Accessories) and run:
sudo fdisk -l (small L)

copy the result here.

---

### Post by halj32 on 2009-12-04
since you are using XP try Patition Magic this program is very good.

---

### Post by Bartender on 2009-12-04
I can't keep it all straight in my head.

Could you post a screenshot?  Have you created an Ubuntu LiveCD yet?  If so, boot from the Ubuntu LiveCD.  Choose "Use Ubuntu without any changes".  When it gets to the desktop, plug in a thumb drive.  Wait for it to be recognized on the desktop and take note of its name.

Next, go to Administration>Gparted Partitioner.  When that comes up it should show a picture of your partitions.

Next, go over to Applications>Accessories>Take Screenshot.  Take a screenshot of your partitions and save the screenshot to the thumb drive.  Right-click on the thumb drive and Eject or Unmount the Volume so that Ubuntu finishes writing to it before you pull it out.

Take that thumb drive to any PC, come back to your thread here, and follow the steps under "Additional Options" > "Attach files", "Manage Attachments" to post the screenshot as an attachment to a post.

It sounds like you have a really screwy partition scheme.  I think the Ubuntu partitioner might be confused.

---

### Post by vikrang on 2009-12-05
I dwnloaded Partition Magic 8.0 (Trial) , but it was giving an error - "Sector not Found".I googled and read about Acronis Partition manager and dwnloaded it to give it a shot...This did the trick! Its a wonderful program clean,neat and user friendly. I merged partition C and G and now it is okay...And I should say, there was absolutely no problem in using this amazing software....All my data is intact and Windows restarted without a problem.....Now I am going to install Ubuntu...Thank you all for your suggestions!

---

### Post by Marvin666 on 2009-12-05
You can't merge 2 partitions unless they are next to each other on the disk.

---

