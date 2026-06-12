---
title: "cannot create new folders in ubuntu 16.10"
date: 2017-02-04
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2017-02-04
My 16.10 system is not allowing me to create new folders except upon the desktop and in Documents.  On the desktop or in Documents, I can right click, and the first item in the drop down menu is ¨new folder¨.  If I navigate to one of my other folders (say Pictures) the option does not exist.  If I create a folder on the desktop and try to drag it to Pictures, it returns to the Desktop.  If I mount and open a disc drive, I cannot create folders, and I cannot check the properties of the disc.

What is wrong?

Thanks.

Caruso

---

### Post by oldfred on 2017-02-04
Post this:
sudo ls -l

       Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)

---

### Post by carusoswi on 2017-02-05
Thanks for the reply.  Here it is:

```
caruso@caruso-G74Sx:~$ sudo ls -l
[sudo] password for caruso: 
total 107368
drwxrwxr-x  2 caruso caruso     4096 Dec 24 08:04 Aspi Driver for WL3
-rw-rw-r--  1 caruso caruso     8957 Oct  8 11:20 Brooklyn.odt
-rw-rw-r--  1 caruso caruso 63193366 Oct 16  2014 crossover_14.0.0-1.deb
drwxr-xr-x 15 caruso caruso     4096 Feb  4 16:31 Desktop
drwxr-xr-x  6 caruso caruso     4096 Jan 28 21:56 Documents
drwxr-xr-x  7 caruso caruso     4096 Jan 28 20:22 Downloads
-rw-r--r--  1 caruso caruso     8980 Mar 28  2015 examples.desktop
drwxr-xr-x  9 caruso caruso     4096 Mar  3  2016 firefox
-rw-rw-r--  1 caruso caruso     2380 Jun 18  2010 getdeb-repository_0.1-1~getdeb1_all.deb.1
-rw-rw-r--  1 caruso caruso 46080764 Mar 20  2015 google-chrome-stable_current_i386.deb
drwxrwxr-x  2 caruso caruso     4096 Mar  5  2016 Handbrake for Windows
-rw-rw-r--  1 caruso caruso   173570 May 30  2015 Hull Registration.pdf
-rw-rw-r--  1 caruso caruso   253229 Jul 20  2015 Lawrence PA Act 34.pdf
-rw-rw-r--  1 caruso caruso    49201 May 30  2015 mozilla.pdf
drwxr-xr-x  3 caruso caruso     4096 Sep 25 10:13 Music
-rw-rw-r--  1 caruso caruso    84990 Jul 20  2015 PA Act 34.pdf
drwxr-xr-x  2 caruso caruso     4096 May 24  2015 Pictures
-rw-rw-r--  1 caruso caruso     2244 Jun 18  2010 playdeb_0.3-1~getdeb1_all.deb.1
drwxr-xr-x  2 caruso caruso     4096 Mar 28  2015 Public
drwxrwxr-x  2 caruso caruso     4096 Jan  3  2016 temp3
drwxr-xr-x  2 caruso caruso     4096 Mar 28  2015 Templates
drwx------  3 caruso caruso     4096 Jan 31  2016 tor-browser_en-US
drwxr-xr-x  2 caruso caruso     4096 Mar 28  2015 Videos
drwxrwxr-x  2 caruso caruso     4096 Jun  7  2015 wdtvlive
caruso@caruso-G74Sx:~$
```

---

### Post by oldfred on 2017-02-05
I have difficulty comparing as I link to all my data partitions & have reset normal permissions.
You own everything which is normal for /home. Sometime users (including me) use sudo and then a file gets saved with root as the owner.

I have reset all ownership & permissions as per link on /home is permissive.

       sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 

I have not had issues with above commands, but a couple of files may need to be different. If issues check these.

 .dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---

### Post by carusoswi on 2017-02-05
Thanks for the reply.  Ran those first two commands, logged out and back in (if that makes a difference).
A couple of folders allow me to right click and find the menu selection for New Folder, but that choice does not appear if I click File from the menu at the top of the screen. If I do right click, when the choice for New Folder is there, I can click it, create and name a new folder.

I have several large physical disc drives in my system to which I am used to being able to create folders as required.  Cannot do that at this moment.  

I have a network drive which, when I click on properties, then permissions, an error message pops up that permissions cannot be determined.  All my other hard drives can be right clicked and permissions are set for create and delete files for me and for all the other choices.

I have never had this problem before, and, frankly, cannot say if it is related to the upgrade or not, but I am guessing that it is related.

I do not know what to do with the .dmrc errors- drs305 and .ICEauthority errors.  I get errors if I copy them to a terminal, so I guess that is not how they are used.

Any additional suggestions would be appreciated.

Again, thank you.

Caruso

---

### Post by yancek on 2017-02-05
> I have a network drive which, when I click on properties, then  permissions, an error message pops up that permissions cannot be  determined. 

What type filesystem is on the network drives, Linux?

---

### Post by oldfred on 2017-02-06
If you can create file one way then ownership & permissions must be ok.
Then you are into Nautilus or whatever file manager you are using type issues, or settings.

And network issues depend a lot on type of networking you are using. I use NFS and never had issues, but part of the set up of NFS you define what folders you share, so you know what will work or not. 
May be best to start a new thread on your network file sharing issues as some others know those issues well and may be able to help.

---

### Post by carusoswi on 2017-02-11
Except for my Ubuntu partitions, all storage is NTFS. I have one networked drive, two internal hard drives in the laptop. I probably should not have mentioned the network drive, because i drew attention away from the central issue. I really don't know where to proceed from here. Problem makes no sense to me. I have been able to check permissions, ownership is me on all, permission read/write on everything. Thanks to all who have replied. Any additional suggestions appreciated.
Caruso

---

### Post by carusoswi on 2017-02-11
So, I gave up and performed a reinstall.  That has not gone well, but I believe that problem should be in a new thread.  Thanks to all who tried to help me.  I've been using Ubuntu regularly since the version 6 days (so long ago, yet so very recent), and I've never experienced a similar problem.  Now my installation is broken, so I've a new project to work on today (system crashes on boot with an error message - couldn't figure out how to capture the screen at that point, so took a photo with my Nexus 5, boot into windows 10, and spent 3 hours chasing down a fix to a but that wouldn't allow my photos to appear when phone was plugged into laptop usb port - got that sorted, thank goodness).
Sometimes life with "devices computer" just go that way.  Patience, a cool head, and looking towards fine folks like those of you who participate in this forum have always proven to save the day.
Once again, thank you for your replies.
Caruso

---

### Post by oldfred on 2017-02-11
You cannot set ownership & permissions on NTFS as it does not support Linux.
But you set a default set of ownership & permissions when you mount it either with fstab or with file browser.

       Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by carusoswi on 2017-02-11
Ok, but, I've never had a problem before this upgrade. I've been using these drives/positions for storage for years over several versions of Ubuntu. Never had to bother setting permission previously. In any event, checking drive properties, they were already set to full read/write by default, so, I don't believe that is the source of the problem, although I could be wrong. Too late, now, as I'm reinstalling Ubuntu. That has not gone smoothly, either. There may be some underlying issues in my Ubuntu install. We'll see. The good part about all this is that I'm free to explore, reinstall, etc. Little danger of data loss. Ubuntu is fairly reliable in that department. Thanks for the reply.
Caruso

---

