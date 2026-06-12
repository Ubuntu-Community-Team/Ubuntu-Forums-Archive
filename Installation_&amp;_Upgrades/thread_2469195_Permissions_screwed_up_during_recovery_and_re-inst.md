---
title: "Permissions screwed up during recovery and re-install"
date: 2021-11-22
forum: Installation &amp; Upgrades
---

### Post by johnfrith1 on 2021-11-22
Hello I'm not a newbie, but know enough to get me into trouble.

My laptop died from a fried battery,  it was a dual boot with Windows and Ubuntu 20.04 on an SSD, with home in it's own partition.
,
My backup to an external drive was a week out of date, so I figured I'd just recover from the SSD which I presumed still worked.

With help, I managed to mount the SSD as a drive on a desktop machine (it has to piggy back on rig that fits an HDD slot). My plan was to copy home and it's files to another HDD, which I would then put as an external drive on my new laptop and copy the files onto the new machine.

However I couldn't copy most of the files from the SSD due to not having permissions. Somehow I managed to copy the files to the HDD (I think that in some directories I had sufficient permission to copy?), 

I then creating a separate partitions for ubuntu  20.04 and for home on my new laptop, I think this was a mistake - I should have recovered the home files before installing Ubuntu on my new laptop which could recognise the old home instead of creating a new one.

However when I tried to copy home from the HDD to home on my new laptop I got permission errors again. At this point I discovered running sudo nautilus and suddenly I could copy where ever I wanted, at the expense of screwing up the permissions royally.

I'm resigned to reformatting the new laptop partitions, and setting up home before I do the Ubuntu install, but I don't understand enough about permission to copy from the old SSD to an HDD and then from the HDD to the new laptop without screwing all the permissions up.

I would really appreciate help (think "a dummies guide to....").

---

### Post by TheFu on 2021-11-23
sudo nautilus is a bad, bad, bad, idea.  Don't run GUI programs under sudo.  There are repercussions. Perhaps not at the time, but later. You will uncover those.

Whenever making backups, we need to be aware of the target file system support for POSIX and we need to be cognizant about maintaining the owner, group, permissions, ACLs and xattrs along with the actual data.  If those other aspects of the file are lost, then we don't have a backup. We just have raw data.  NTFS and FAT32 and exFAT don't support any of the extra file data we need. In fact, they don't even support the same names for files and directories.

Summary:
[LIST]
[*]Don't use sudo with any GUI program.
[*]When making backups and when restoring backups, use tools that retain the owner, group, permissions, ACLs and xattrs along with the actual data.
[*]Don't use NTFS, fat32, exfat for backup storage.
[/LIST]
*@$# - there are always exceptions, but for now, until you understand more, just don't.

Backups can be as simple as using **sudo cp -rp** or **sudo rsync -avz** or using a real backup tool with sudo (just not a GUI).  Some programs in the menu system will elevate privileges using alternatives to sudo, which are safe.  Many GUI backup programs are only supposed to be used for 1 user's HOME and for that, it isn't too bad, provided non-native file systems aren't used.  You can attempt to fix all the files in your HOME using this command:
```
sudo chown -R $USER:$USER $HOME
```
That should be safe, provided you didn't go crazy using *sudo name-of-gui-program* with too many different programs.  Don't use sudo with file managers. Just don't.

I think in 21.04 and later, Canonical altered the default behavior of sudo so the HOME directory will be set based on the new, elevated, userid .... this will be helpful and make using sudo with a GUI not-so-dangerous.

---

### Post by yancek on 2021-11-23
You should not have problems copying data/files FROM a partition but could when copying to  a partition if.  On a standard system, a user should be able to write/copy to his/her home partition without problems. 

>  My plan was to copy home and it's files to another HDD, which I would  then put as an external drive on my new laptop and copy the files onto  the new machine.
 

Copying /home/usera while logged in as user should not present a problem nor should logging in as userb and copying userb files to it's /home partition.

---

### Post by TheFu on 2021-11-23
> **yancek said:**
> You should not have problems copying data/files FROM a partition but could when copying to  a partition if.  On a standard system, a user should be able to write/copy to his/her home partition without problems. 



Copying /home/usera while logged in as user should not present a problem nor should logging in as userb and copying userb files to it's /home partition.

True, but if using **sudo nautilus** or any GUI file manager - the owner won't be the user most likely.

---

### Post by johnfrith1 on 2021-11-23
> **yancek said:**
> Copying /home/usera while logged in as user should not present a problem nor should logging in as userb and copying userb files to it's /home partition.

I don't think I made clear one critical point. The SSD with my source user data isn't bootable, so I'm booting from a USB stick to access it. 

So say the original data on my SSD is usera. What I'd like to do is
1) boot from USB (say as userb) and copy usera data to an external NTFS HDD. Then 
2) move the HDD to be an external drive to my laptop with a couple of blank partitions. Again boot from a USB (so now I'm user c), and copy usera files onto a blank partition.
3) Install Ubuntu on the other blank partition, and point it to the partition with usera data.
4) Boot my laptop and start my normal life again.

Alternative idea. Is there a way for me to boot from a usb but somehow make home as the partition with my original data - so I would be usera and be able to copy files?

---

### Post by johnfrith1 on 2021-11-23
Actually I just tried your sudo chown -R $USER:$USER $HOME

and it's solved a lot of my problems.  A big hooray from me to TheFu. If I ever get to meet you, I'll buy you beers all night!




I've learned my lesson not to mess with chown and not to sudo a gui!
I'll try and digest the rest of your post too.

---

### Post by TheFu on 2021-11-23
> **johnfrith1 said:**
> Actually I just tried your sudo chown -R $USER:$USER $HOME

and it's solved a lot of my problems.  A big hooray from me to TheFu. If I ever get to meet you, I'll buy you beers all night!

I've learned my lesson not to mess with chown and not to sudo a gui!
Ill try and digest the rest of your post too.

Sadly, I think lots of files still have the wrong permissions that only a solid backup would be able to restore - a backup that includes .... you guess it ... the owner, group, permissions, ACLs, and xattrs.  And it would be really nice if the backups were versioned, so you could see the changes not just to the data, but to the  .... you guessed it ... the owner, group, permissions, ACLs, and xattrs over time.  There are some files that just won't work in your HOME if they have the wrong permissions, even if the owner is correct.

And there are exceptions for when using sudo with a GUI is ok, but until you are at the point of that understanding, best to just not do it.  And by that time, you won't need to do it anyway.  There is 1 time I can think of off the top of my head that the alternatives just aren't worth fighting - that using **sudo gparted**.  NEVER use *sudo gedit* (or any other GUI editor) like lots of the tutorials show.  To edit system files, use **sudoedit /the/path/to/the/file**.  **sudo vim** or **sudo nano** are safe, but it is best to make it a habit to use **sudoedit** always.

---

