---
title: "Made mistake unsuccessfully upgraded to 8.04, how to go back"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by Kipton Moravec on 2008-03-28
I have been running 6.06 LTS. 

I was in the ubuntu user email list to run gksu "update-manager -c -d" 

when nothing happened from using gksu "update-manager -c" 

It looked like it wanted to jump me from 6.06 to 8.04.

I was assured on the list that was O.K.

It took all evening, and kept stopping and asking questions. 

It could not find stupid things like evolution-6.0.png and a couple of other icons. They were replaced at the top of the gnome window with yellow triangles with question marks. 

It looks like it failed to install, so it tried to revert back.

In the process of reverting back it hung. And did not do anything for more than an hour. So I rebooted.

When it boots I get
Kernal Panic - not synching VFS: unable to mount root FS on unknown block (0,0)

If I type <esc> with Grub, I can boot an earlier version of the kernal. The default that panics is 2-6-24-12-386

If I go to 2-6-15-51-386 recovery mode, it gets to the recovery menu
I have three options:

Resume normal boot

Drop to root shell prompt

Try to fix xserver

If I try resume normal boot it gets to:
Running Local Boot Scripts                    [OK]
then hangs. No disk activity.

crtl-alt-del shuts down gnome manager and it looks  like it shuts down gracefully


If I try to fix X server 
it says dpkg-reconfigure xserver-xorg broken or not fully installed

I can drop to a root shell prompt but I don't know what to do as I am a GUI type of person.

What should I do?

At this point I would be very very happy to go back to 6.06 LTS. 

I need a working system,(I do not care which version)  and anything is better than nothing. I called a friend and he said he never upgrades if it is working. I wish I had talked to him first.

I have a working Windows XP computer I can create CDs on if I need to.

I need to know what is the best advice for where I am now. I do not want to format the disks as I have more than a year of email and work on the computer.  The \home directory is in its own partition. I would like to not touch that.

What is the best advice for someone who is not an expert?

Kip

---

### Post by kellemes on 2008-03-28
Well.. my advice would be to backup your data (/home) and reinstall the Ubuntu version you want.
It's by far the easiest way.. Backup /home at least and think about some other files you may want to use as an example for your next install.. maybe /etc/X11/xorg.conf or /etc/fstab .. whatever..
I'd go 7.10 probably, or give it a shot anyway..

Listen, never forget to create backups of your data, you're having a great deal of luck not losing it all!

---

### Post by Kipton Moravec on 2008-03-28
O.K. now for the stupid question. 

I know how to backup from the GUI how do I backup from the command prompt?

I have a 100 GB USB disk and a 400 GB second disk normally mounted as /home/backup where my simple backups normally go. My main disk ia about 100 GB with a 65 GB \home partition, and a 35GB partition for the OS. And a swap.

If I copy all the data to the big disk drive for backup and disconnect it I should be safe. I can do that with midnight commander.

What else should I save? I have a custom samba script. But I am not sure where it is. I guess I could search for samba.conf

I think I will go back to 6.06 LTS, since that is partially backed up in my simple backup.

Kip

---

### Post by kellemes on 2008-03-28
> **Kipton Moravec said:**
> O.K. now for the stupid question. 

I know how to backup from the GUI how do I backup from the command prompt?

I have a 100 GB USB disk and a 400 GB second disk normally mounted as /home/backup where my simple backups normally go. My main disk ia about 100 GB with a 65 GB \home partition, and a 35GB partition for the OS. And a swap.

If I copy all the data to the big disk drive for backup and disconnect it I should be safe. I can do that with midnight commander.

What else should I save? I have a custom samba script. But I am not sure where it is. I guess I could search for samba.conf

I think I will go back to 6.06 LTS, since that is partially backed up in my simple backup.

Kip

Well, you pretty much understand what to do ;-)

I'm not sure where your samba stuff is actually is.. you need to search for it.
One way of searching from the commandline..
update your package-database
```
sudo updatedb
```
```
locate <searchexpression>
```
Midnightcommander surely has a searchoptions also..

copying from the commandline..
```
cp /path/filename <destination>
```
moving from the commandline..
```
mv /path/filename <destination>
```

Personally I have about 325 million copies of /etc/X11/xorg.conf because it took me about half my life to set it up. ;-)
Also I backup some files as a reference for a next install, so I don't simply copy them back, that can be dangerous.
/etc/fstab (for automounting devices)
/boot/grub/menu.lst (bootloader menu)
/etc/apt/sources.list (since I have a couple of extra repositories I use)
/etc/apt/preferences (I use it to "pin" specific packages.. ergo.. don't want them upgraded)

Just to be sure you can backup the /etc directory.. it's 13 Mb in my case.

Just think of software you spend a lot of time on configuring and try to find the configuration-files.. just like with Samba.

Good luck.

Edit:
In your /home you also have your profile-folders for thunderbird/firefox. May also be very important since loosing all of your emails/bookmarks may be hurting.

---

### Post by Kipton Moravec on 2008-03-28
I think I have all that backed up using simple backup. But I will copy all of those just in case.

I tried to download the CD from gegabytes and the download was 1 second and was 115K bytes. I tried about 3 tmes and got different sizes all about 1 second worth of download. I switched to western michigan and it is downloading correctly. (Always something).

I think I have everything backed up. I use the program Simple Backup every night at 1:00 a.m. and it makes incrementals every night and a full backup every 2 weeks. I just do not know how to start it without the GUI working. I only have command line working at the moment.

And in addition  my project file is backed up to another computer when I think about it. I also back it up to DVD every couple of months.

Have you ever had to recover using simple backup? have you been happy with it? Or do you use something different?

Kip

---

### Post by louieb on 2008-03-28
Since you have a separate /home partition. (This is one great reason to have one).  You can reinstall Dapper. Only this time you''ll use manual partitioning tell the  partition step  not to format  /home (preserve the data).  

Kind of a pain to reinstall the OS and all the programs you need. But at least you get to keep you data. 

Just remember to use the same user name you used in the original install. 
one odd thing about Linux is users are known by the user id such as lou george .. and they also have a 4 digit uid.  If  you have more than one user you will need there uid when you add them back. the uid can be found in /etc/group. 

Once Dapper is installed and updated. You can check your data if you find things missing the install simple backup and look at the restore options. 

I use partimage for my backup,  others use tar or SImple backup or something else. Each has its advantages and disadvantages.

---

### Post by Kipton Moravec on 2008-03-30
That is what I did. I went back to 6.06 LTS and it made me reformat \boot \ and swap partitions. \home and the other disk did not reformat.  

I had backed up everything to my other disk, but did not need anything from the backup yet.

Everything is working except my printer. If I remember correctly I had to go somewhere to fget the driver for the HP LaserJet 3050. The printer is on the Windows XP computer.

Thanks for all the help.

---

